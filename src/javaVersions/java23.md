# ✅ Sequenced Collections in Java
    Provide a uniform API for collections with defined encounter order, i.e., collections where 
    elements have a meaningful first and last element (like List, Deque, or ordered Set).
### 📘 1. SequencedCollection<E> Interface
- Introduced in Java 21 (Preview)
- Superinterface for ordered collections (like List, Deque, LinkedHashSet, etc.)
### Methods    
    E getFirst();
    E getLast();
    void addFirst(E e);
    void addLast(E e);
    E removeFirst();
    E removeLast();
    SequencedCollection<E> reversed();

### 📗 2. SequencedList<E> Interface
    •Extends List<E> and SequencedCollection<E>
    •Meant for lists with a defined order (like ArrayList, LinkedList)
    •Inherits all SequencedCollection methods

### 📙 3. SequencedSet<E> Interface
    •Extends Set<E> and SequencedCollection<E>
    •Ensures no duplicates and maintains order
    •Typical implementation: LinkedHashSet

