 🔴🔵☑️✔️ ➡️ ✓→•←⁕⁂※⁜‣
# Arrays
- An array is a container that holds a fixed number of elements of a single type (e.g., int, String,
         or any object type).
- Arrays are objects in Java, so they are allocated on the heap and can be null. 
- Arrays are immutable in size once created (their length cannot change), but their elements can be modified.


### ➡️ Different Ways to Create Arrays

##### ✅ 1. Using the new keyword with specified size

```java
int[] numbers = new int[5]; // creates an array of size 5 with default values (0)
```

##### ✅ 2. Array Initialization with values (static initialization)
```java
int[] numbers = {1, 2, 3, 4, 5}; // size automatically determined
String[] names = {"Alice", "Bob", "Charlie"};

```
##### ✅ 3. Using new keyword with values (dynamic initialization with values)
```java
int[] numbers = new int[]{10, 20, 30, 40}; // explicitly using `new` with values

int[] arr;
arr = {1, 2, 3}; // ❌ invalid
arr = new int[]{1, 2, 3}; // ✔️ correct

```
##### ✅ 5. Using Array Utility Methods (e.g., Arrays.copyOf)
```java
import java.util.Arrays;

int[] original = {1, 2, 3};
int[] copy = Arrays.copyOf(original, 5); // copy of length 5, last 2 values will be 0

```
##### ✅ 6. Multidimensional Arrays

```java
- ➤ 2D Array
int[][] matrix = new int[3][3]; // 3x3 matrix with all values 0

- ➤ 2D Array with values
int[][] matrix = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
};

```

##### ✅ 7. Jagged Arrays (Arrays of arrays with different lengths)
```java
int[][] jagged = new int[3][];
jagged[0] = new int[]{1, 2};
jagged[1] = new int[]{3, 4, 5};
jagged[2] = new int[]{6};

```
##### ✅ 8. Anonymous Arrays
```java
System.out.println(sum(new int[]{10, 20, 30}));

public static int sum(int[] arr) {
    int sum = 0;
    for (int num : arr) sum += num;
    return sum;
}

```

### ➡️ Arrays Methods

##### java.lang.Object
- length (Field)
- clone()
- equals(Object obj)
- hashCode()
- toString()
- notify()
- wait()

##### java.util.Arrays
- **Comparison Methods**  
   `equals()`
- **Hash Code Methods**  
    `hashCode()`
- **String Representation Methods**
     `toString()`
- **Deep Comparison, Hash Code, and String Representation (for Multi-Dimensional Arrays)**  
     `deepEquals(Object[] a1, Object[] a2)` – Checks if two arrays (including nested arrays) are deeply equal.
     `deepHashCode(Object[] a)` – Computes a hash code for an array, including nested arrays.
     `deepToString(Object[] a)` – Returns a string representation of an array, including nested arrays (e.g., "[[1, 2], [3, 4]]").
- **Sorting Methods**   
     `sort()`
- **Parallel Sorting Methods**  
     `parallelSort(types[] a)` – Sorts a types array in parallel (Java 8+).
- **Binary Search Methods**  
     `binarySearch(type[] a, byte key)`` – Searches for a key in a sorted type array.
- **Filling Methods**  
     `fill()`
- **Copying Methods** ☑️   
     `copyOf(arr, int newLength)` – Copies a type array to a new array of specified length.
     `Arrays.copyOfRange(arr, from, to)` - closest equivalent to slice() in js.
      `list.subList(start, end)` - Works for List<T> (ArrayList)
- **Stream Conversion Methods**    
     `stream(Type[] array)` – Converts a Type array to a DoubleStream (Java 8+).
- **Mismatching Methods**    
     `mismatch(Type[] a, Type[] b)` – Finds the index of the first mismatch between two Types arrays (Java 9+).
- **Spliterator Methods**  
     `spliterator(Type[] array)` – Creates a Spliterator.OfType for a Type array (Java 8+).
- **Set All Methods**  
     `setAll(Type[] array, TypeToTypeFunction generator)` – Sets all elements of a Type array using a generator function (Java 8+).
- **Parallel Set All Methods**  
     `parallelSetAll(Type[] array, TypeToTypeFunction generator)` – Sets all elements of a Type array in parallel (Java 8+).
- **Parallel Prefix Methods**  
     `parallelPrefix(Type[] array, TypeBinaryOperator op)` – Computes a parallel prefix (cumulative operation) on a Type array (Java 8+).
- **As List Method** 
     `asList(T... a)` – Returns a fixed-size List backed by the specified array.