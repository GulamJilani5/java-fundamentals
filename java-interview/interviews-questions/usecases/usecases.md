⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Issue 1

### ➡️ Problem

“We faced a performance issue in our Spring Boot application where a simple read query was taking around `10ms` to execute. The surprising part was that there was no heavy logic—just a basic findById() query using a custom `@Query.`”

- **Repository**

```java
    @Repository
    public interface UserRepository extends JpaRepository<User, Long> {

        @Query("SELECT u FROM User u WHERE u.id = :id")
        Optional<User> findById(@Param("id") Long id);
    }

```

- **Service**

```java

  @Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    @Transactional
    public Optional<User> getUserById(Long id) {
        return userRepository.findById(id);
    }
}

```

- The root cause was the use of `@Transactional` on a read-only query.

### ➡️ Why Did This Slow Things Down?

- When we add `@Transactional`, Spring:

  - Creates a **transactional proxy** around the bean
  - Opens a new database transaction (even for read operations)
  - Tracks entity state for changes (**Dirty Checking**)
  - Performs synchronization and possible flush checks

- This overhead is unnecessary for **read-only queries**, and that’s why the execution time increased.

### ➡️ The Fix – Use @Transactional(readOnly = true)

- Instead of creating a transaction with full overhead, we mark it as read-only:

- **Service**

```java
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    @Transactional(readOnly = true)   // ✅ Best practice for read operation
    public Optional<User> getUserById(Long id) {
        return userRepository.findById(id);
    }
}

```

### ➡️ Impact

- Huge performance gain for read-heavy applications
- If app serves **1M** `requests/day`, saving `~9.8ms` per **request = 2.7 hours of CPU time saved daily**
- Less pressure on DB & application threads

# ⏺️ Issue 2

### ➡️ The Problem

- The API was written using Java Streams everywhere for data processing.
  However, the implementation had inefficiencies, such as:

  - Long chained Stream operations (`map → filter → collect → stream again`)
  - Creating multiple intermediate collections unnecessarily
  - Using sequential streams for large datasets
  - Using `Collectors.toList()` which internally creates extra copies

- The code looked clean and modern, but it wasn’t optimized for high-traffic scenarios.

### ➡️ Why Did This Slow Things Down?

- `Collectors.toList()` overhead
  - Often creates a new modifiable list copy → more memory + extra time cost
- Too many Stream operations in one pipeline
  - Each Stream step adds overhead through lambdas, function objects, and context switching
- Intermediate collections created
  - Increased memory allocation → more garbage collection → slower performance under load
- Sequential processing for heavy tasks
  - Only 1 thread utilized, leaving CPU cores idle, causing delay under high traffic
- Streams used for simple logic

  - Streams add complexity and overhead compared to a simple loop which is faster in hot paths

- **In short:** Streams introduce hidden CPU + memory overhead. During traffic spikes, these costs multiply, slowing down response time.

### ➡️ The Fix and Impact

| Fix Implemented                                                              | Impact Achieved                                         |
| ---------------------------------------------------------------------------- | ------------------------------------------------------- |
| Replaced heavy Stream chains with optimized loops where performance mattered | Reduced CPU usage and faster execution                  |
| Removed unnecessary intermediate `collect()` calls                           | Lower memory consumption and fewer GC pauses            |
| Used `parallelStream()` only for safe CPU-bound operations                   | Leveraged multi-core processing for faster results      |
| 🔴 Switched from `Collectors.toList()` to `toUnmodifiableList()`             | Eliminated extra copying + improved immutability safety |

### ➡️ Measured Outcome

- ~30–35% faster API response time
- Lower CPU and GC overhead
