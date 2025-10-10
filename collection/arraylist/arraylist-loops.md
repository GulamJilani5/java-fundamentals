# Different Ways To Loop Over An ArrayList

 ### ➡️1)For Loop (Index-Based)
    for (int i = 0; i < list.size(); i++) {
        System.out.println(list.get(i));
    }

 ### ➡️2)Enhanced For Loop (For-Each)
     for (String item : list) {
        System.out.println(item);
     }

 ### ➡️3)While Loop with Index
      int i = 0;
      while (i < list.size()) {
          System.out.println(list.get(i));
          i++;
      }

 ### ➡️4)forEach Method (Java 8+)
        list.forEach(item -> System.out.println(item));
        // Or: list.forEach(System.out::println);

 ### ➡️5)Stream API (Java 8+)
        list.stream().forEach(System.out::println);
        list.stream()
            .filter(s -> s.startsWith("A"))
            .forEach(System.out::println);
        list.parallelStream().forEach(System.out::println);

 ### ➡️6) Iterator
       Iterator<String> iterator = list.iterator();
       while (iterator.hasNext()) {
           String item = iterator.next();
           System.out.println(item);
           // Can remove: iterator.remove();
       }

 ### ➡️7)ListIterator
       ListIterator<String> listIterator = list.listIterator();
       while (listIterator.hasNext()) {
           String item = listIterator.next();
           System.out.println(item);
           // Can modify: listIterator.set("NewValue");
       }

 ### ➡️8)Spliterator (Java 8+)
       Spliterator<String> spliterator = list.spliterator();
       spliterator.forEachRemaining(System.out::println);