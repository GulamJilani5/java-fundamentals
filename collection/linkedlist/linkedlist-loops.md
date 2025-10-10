🔴🔵☑️✔️ ➡️ ✓→•←⁕⁂※⁜‣

# Different Ways To Loop Over

 ### ➡️1. Using forEach(Consumer action) (Java 8+)
      linkedList.forEach(item -> System.out.println(item));

 ### ➡️2. Using Java Streams (Java 8+)
       linkedList.stream().forEach(System.out::println);          // Sequential
       linkedList.parallelStream().forEach(System.out::println);  // Parallel

 ### ➡️3. Using Enhanced For Loop (For-Each Loop)
      for (String item : linkedList) {
          System.out.println(item);
      }

 ### ➡️4. Using Classic For Loop (by Index)
      for (int i = 0; i < linkedList.size(); i++) {
          System.out.println(linkedList.get(i));
      }
      // Not efficient in LinkedList (O(n^2) time), avoid for large lists

 ### ➡️5. Using Iterator
      Iterator<String> iterator = linkedList.iterator();
      while (iterator.hasNext()) {
          System.out.println(iterator.next());
      }

 ### ➡️6. Using Descending Iterator
      Iterator<String> descIterator = linkedList.descendingIterator();
      while (descIterator.hasNext()) {
          System.out.println(descIterator.next());
      }

 ### ➡️7. Using ListIterator (Bidirectional)
       ListIterator<String> listIterator = linkedList.listIterator();
       while (listIterator.hasNext()) {
           System.out.println(listIterator.next());
       }
       while (listIterator.hasPrevious()) {
           System.out.println(listIterator.previous());
       }

 ### ➡️8. Using forEachRemaining() (on Iterator)
       Iterator<String> it = linkedList.iterator();
       it.forEachRemaining(System.out::println);















