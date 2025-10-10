🔴🔵☑️✔️ ➡️ ✓→•←⁕⁂※⁜‣

# Different Ways To Create Arraylist

 ### ➡️1) Basic Creation - Generic ArrayList (with type specification):
    import java.util.ArrayList;
    ArrayList<String> list = new ArrayList<>();

### ➡️2) Specifying Initial Capacity - With a defined initial capacity
    ArrayList<Integer> list = new ArrayList<>(20);

### ➡️3) 🔴From Another Collection - Using a Collection (e.g., another List or Set)
    import java.util.Arrays;
    ArrayList<String> list = new ArrayList<>(Arrays.asList("A", "B", "C"));

### ➡️4) Using List.of (Java 9+) and Constructor - With immutable List to ArrayList:
    ArrayList<String> list = new ArrayList<>(List.of("X", "Y", "Z"));

# Different Methods of ArrayList
### ➡️1) Add
    boolean add(E e):
    boolean addAll(Collection<? extends E> c): Appends all elements from the specified collection to the end.

### ➡️2) Accessing Elements
      •E get(int index): Returns the element at the specified index
            String item = list.get(0); // Gets element at index 0
      •int indexOf(Object o): Returns the index of the first occurrence of the specified element, or -1 if not found.
            int index = list.indexOf("Apple"); // Returns index of "Apple"
      •int lastIndexOf(Object o): Returns the index of the last occurrence of the element, or -1 if not found.
            int lastIndex = list.lastIndexOf("Apple");
  ###### Stream Support (Java 8+)
        •Stream<E> stream(): Returns a sequential stream with the list as its source.
             list.stream().forEach(System.out::println); // Streams and prints elements
        •Stream<E> parallelStream(): Returns a parallel stream for parallel processing
             list.parallelStream().forEach(System.out::println);

### ➡️3) Remove
      •E remove(int index):
          String removed = list.remove(0); // Removes element at index 0
      •boolean remove(Object o):
          list.remove("Apple"); // Removes "Apple"
      •boolean removeAll(Collection<?> c): Removes all elements that are contained in the specified collection.
          list.removeAll(Arrays.asList("Banana", "Grape"));
      •boolean retainAll(Collection<?> c): Retains only the elements contained in the specified collection (removes others).
          list.retainAll(Arrays.asList("Apple", "Orange"));
      •void clear(): Removes all elements from the list.
      •boolean removeIf(Predicate<? super E> filter) (Java 8+): Removes all elements that satisfy the given predicate.

### ➡️4) Updating Elements
      •E set(int index, E element): Replaces the element at the specified index with the new element and returns the old element.
         String old = list.set(1, "Kiwi"); // Replaces element at index 1 with "Kiwi"

### ➡️5) Checking Elements
      •boolean contains(Object o): Returns true if the list contains the specified element.
          boolean hasApple = list.contains("Apple");
      •boolean isEmpty(): Returns true if the list is empty.
          boolean empty = list.isEmpty();
      •int size(): Returns the number of elements in the list.
          int size = list.size();

### ➡️6) Bulk Operations
       •void replaceAll(UnaryOperator<E> operator) (Java 8+): Replaces each element with the result of applying the operator.
          list.replaceAll(String::toUpperCase); // Converts all elements to uppercase
       •void sort(Comparator<? super E> c) (Java 8+): Sorts the list according to the specified comparator.
          list.sort(Comparator.naturalOrder()); // Sorts in natural order.

### ➡️7) Converting and Copying
       •Object[] toArray(): Returns an array containing all elements in the list.
          Object[] array = list.toArray();
       •T[] toArray(T[] a): Returns an array of the specified type containing all elements.
          String[] stringArray = list.toArray(new String[0]);
       •List<E> subList(int fromIndex, int toIndex): Returns a view of the portion of the list between fromIndex (inclusive) and toIndex (exclusive).
          List<String> sub = list.subList(1, 3); // Gets elements from index 1 to 2

### ➡️8) Miscellaneous
      •Iterator<E> iterator(): Returns an iterator over the elements in the list.
         Iterator<String> iterator = list.iterator();
      •ListIterator<E> listIterator(): Returns a list iterator (supports bidirectional traversal).
         ListIterator<String> listIterator = list.listIterator();
      •ListIterator<E> listIterator(int index): Returns a list iterator starting at the specified index.
         ListIterator<String> listIterator = list.listIterator(2);
      •Spliterator<E> spliterator() (Java 8+): Creates a spliterator for parallel processing.
         Spliterator<String> spliterator = list.spliterator();
      •void ensureCapacity(int minCapacity): Increases the capacity to at least the specified amount.
         list.ensureCapacity(50); // Ensures capacity for 50 elements
      •void trimToSize(): Trims the capacity to the current size of the list.
         list.trimToSize(); // Reduces capacity to match size


