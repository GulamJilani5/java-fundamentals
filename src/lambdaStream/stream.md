# Stream Creation / Converting to Stream (Source)
   ### ➡️From Collections
              •collection.stream()
              •collection.parallelStream() 

   ### ➡️From Arrays
              •Arrays.stream(array)
              •Stream.of(array)

   ### ➡️From Values
              •Stream.of(1, 2, 3)
              •Stream.generate(Supplier)
              •Stream.iterate(seed, unaryOperator)
              •IntStream.range(1, 10)
              •LongStream.rangeClosed(1, 10)

🔴🔵☑️✔️ ➡️
✓→•←⁕⁂※⁜‣

 # Intermediate Operations
  
| Method                 | Description                                     |
|------------------------| ----------------------------------------------- |
| ➡️`filter(Predicate)`  | Filters elements that match a condition         |
| ➡️`map(Function)`      | Transforms each element                         |
| ➡️`flatMap(Function)`  | Flattens nested structures                      |
| ➡️`sorted()`           | Sorts elements in natural order                 |
| ➡️`sorted(Comparator)` | Sorts elements with a comparator                |
| ➡️`distinct()`         | Removes duplicates                              |
| ➡️`limit(n)`           | Limits the stream to first `n` elements         |
| ➡️`skip(n)`            | Skips the first `n` elements                    |
| ➡️`peek(Consumer)`     | Performs an action for debugging (like logging) |




# Terminal Operations
| Method                 | Description                                        |
|------------------------| -------------------------------------------------- |
| ➡️`forEach(Consumer)`    | Performs an action for each element                |
| ➡️`collect(Collector)`   | Collects elements into a collection (e.g., List)   |
| ➡️`toArray()`            | Converts to an array                               |
| ➡️`reduce(...)`          | Reduces stream to a single value (e.g., sum)       |
| ➡️`count()`              | Counts number of elements                          |
| ➡️`anyMatch(Predicate)`  | Returns `true` if any match the condition          |
| ➡️`allMatch(Predicate)`  | Returns `true` if all match                        |
| ➡️`noneMatch(Predicate)` | Returns `true` if none match                       |
| ➡️`findFirst()`          | Returns the first element (if present)             |
| ➡️`findAny()`            | Returns any element (useful with parallel streams) |
| ➡️`min(Comparator)`      | Finds minimum element                              |
| ➡️`max(Comparator)`      | Finds maximum element                              |

          


