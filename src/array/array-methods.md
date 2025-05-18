 🔴🔵☑️✔️ ➡️ ✓→•←⁕⁂※⁜‣
# Arrays
       -An array is a container that holds a fixed number of elements of a single type (e.g., int, String,
         or any object type).
       -Arrays are objects in Java, so they are allocated on the heap and can be null.
       -Arrays are immutable in size once created (their length cannot change), but their elements can be modified.

 ### java.lang.Object
        •length (Field)
        •clone()
        •equals(Object obj)
        •hashCode()
        •toString()
        •notify()
        •wait()

 ### java.util.Arrays
     ➡️Comparison Methods
       •equals()
      
      ➡️Hash Code Methods
        •hashCode()
   
      ➡️String Representation Methods
         •toString()

      ➡️Deep Comparison, Hash Code, and String Representation (for Multi-Dimensional Arrays)
         •deepEquals(Object[] a1, Object[] a2) – Checks if two arrays (including nested arrays) are deeply equal.
         •deepHashCode(Object[] a) – Computes a hash code for an array, including nested arrays.
         •deepToString(Object[] a) – Returns a string representation of an array, including nested arrays (e.g., "[[1, 2], [3, 4]]").

      ➡️Sorting Methods
         •sort()

      ➡️Parallel Sorting Methods
         •parallelSort(types[] a) – Sorts a types array in parallel (Java 8+).

      ➡️Binary Search Methods
         •binarySearch(type[] a, byte key) – Searches for a key in a sorted type array.

      ➡️Filling Methods
         •fill()

      ➡️Copying Methods
         •copyOf(Type[], int newLength) – Copies a type array to a new array of specified length.

      ➡️Stream Conversion Methods
         •stream(Type[] array) – Converts a Type array to a DoubleStream (Java 8+).

      ➡️Mismatching Methods
         •mismatch(Type[] a, Type[] b) – Finds the index of the first mismatch between two Types arrays (Java 9+).

      ➡️Spliterator Methods
         •spliterator(Type[] array) – Creates a Spliterator.OfType for a Type array (Java 8+).

      ➡️Set All Methods
         •setAll(Type[] array, TypeToTypeFunction generator) – Sets all elements of a Type array using a generator function (Java 8+).

      ➡️Parallel Set All Methods
         •parallelSetAll(Type[] array, TypeToTypeFunction generator) – Sets all elements of a Type array in parallel (Java 8+).

      ➡️Parallel Prefix Methods
         •parallelPrefix(Type[] array, TypeBinaryOperator op) – Computes a parallel prefix (cumulative operation) on a Type array (Java 8+).

      ➡️As List Method
         •asList(T... a) – Returns a fixed-size List backed by the specified array.