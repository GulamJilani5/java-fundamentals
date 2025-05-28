# ✅ Top-Level: Collection Interface

 ### ✅ 1) List<E> Interface
   🔹 List has NO **Subinterfaces** defined in the Java Collections Framework.
    However, the **ListIterator** interface is used with lists for bidirectional traversal, but it's not 
    a subinterface of List.

  ### ✅ 2) Set<E> Interface
        Set<E>
            ├── SortedSet<E>
            └── NavigableSet<E>

##### 🔹 Implementations:
| Interface      | Implementation Classes     |
| -------------- | -------------------------- |
| `Set`          | `HashSet`, `LinkedHashSet` |
| `SortedSet`    | `TreeSet`                  |
| `NavigableSet` | `TreeSet`                  |

  ### 3) Queue<E> Interface
        Queue<E>
              └── Deque<E>
##### 🔹 Implementations:
| Interface | Implementation Classes        |
| --------- | ----------------------------- |
| `Queue`   | `PriorityQueue`, `LinkedList` |
| `Deque`   | `ArrayDeque`, `LinkedList`    |







# Java Collections Framework – Complete Hierarchy
    Iterable<T>
    │
    └── Collection<E>
    ├── List<E>
    │   ├── ArrayList
    │   ├── LinkedList  (also implements Deque)
    │   ├── Vector
    │   └── Stack       (extends Vector)
    │
    ├── Set<E>
    │   ├── HashSet
    │   ├── LinkedHashSet (maintains insertion order)
    │   └── SortedSet<E>
    │       └── NavigableSet<E>
    │           └── TreeSet
    │
    └── Queue<E>
    ├── LinkedList   (also List, Deque)
    ├── PriorityQueue
    └── Deque<E>
    ├── ArrayDeque
    └── LinkedList (again)
  ###  Collection Interfaces and its Implementing classes.
| **Interface**   | **Subinterfaces**                 | **Implementing Classes**                     |
| --------------- | --------------------------------- | -------------------------------------------- |
| `Collection<E>` | `List<E>`, `Set<E>`, `Queue<E>`   | -                                            |
| `List<E>`       | *None*                            | `ArrayList`, `LinkedList`, `Vector`, `Stack` |
| `Set<E>`        | `SortedSet<E>`, `NavigableSet<E>` | `HashSet`, `LinkedHashSet`, `TreeSet`        |
| `Queue<E>`      | `Deque<E>`                        | `PriorityQueue`, `LinkedList`, `ArrayDeque`  |
| `Deque<E>`      | *None*                            | `ArrayDeque`, `LinkedList`                   |


# ✅ Map Hierarchy (Not a subinterface of Collection)
    Map<K, V>
    ├── HashMap
    │   └── LinkedHashMap   (maintains insertion order)
    ├── SortedMap<K, V>
    │   └── NavigableMap<K, V>
    │       └── TreeMap
    ├── Hashtable           (legacy, synchronized)
    └── ConcurrentMap<K, V>
    └── ConcurrentHashMap
    └── ConcurrentNavigableMap<K, V> (interface only)



# List, Set, Queue, Map and Stack: 
| Feature / Type             | **List**                            | **Set**                                                   | **Queue**                                          | **Map**                                                          | **Stack**                         |
| -------------------------- | ----------------------------------- | --------------------------------------------------------- | -------------------------------------------------- | ---------------------------------------------------------------- | --------------------------------- |
| **Interface Type**         | `List<E>`                           | `Set<E>`                                                  | `Queue<E>`                                         | `Map<K, V>`                                                      | `List<E>` (via `Stack` class)     |
| **Ordering**               | Maintains **insertion order**       | No guaranteed order (except `LinkedHashSet` or `TreeSet`) | Usually FIFO (first-in, first-out)                 | No ordering for keys (unless using `LinkedHashMap` or `TreeMap`) | LIFO (last-in, first-out)         |
| **Duplicates**             | ✅ Allows duplicates                 | ❌ Does **not** allow duplicates                           | ✅ May allow duplicates (depends on implementation) | ❌ Duplicate keys not allowed, values can be duplicated           | ✅ Allows duplicates               |
| **Access Pattern**         | Indexed access (get by index)       | Access via iterator                                       | Insert/Remove at head or tail                      | Key-based access (`get(key)`)                                    | Access using `push()` and `pop()` |
| **Common Implementations** | `ArrayList`, `LinkedList`, `Vector` | `HashSet`, `LinkedHashSet`, `TreeSet`                     | `LinkedList`, `PriorityQueue`, `ArrayDeque`        | `HashMap`, `LinkedHashMap`, `TreeMap`, `Hashtable`               | `Stack` (extends `Vector`)        |
