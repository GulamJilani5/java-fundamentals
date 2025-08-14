🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️
☑️ • ‣ → ⁕ ⏺️

# ⏺️Java 21 (September 2023)

Java 21, an LTS release, introduced significant concurrency and expressiveness improvements, building on preview features from earlier versions.

### ➡️ Virtual Threads (Finalized):🟠🟠🟠

### ➡️ Record Patterns (Finalized):🟠

### ➡️ Pattern Matching for switch (Finalized):

### ➡️ Unnamed Patterns & Variables(Preview)

### ➡️ Sequenced Collections(Finalized)::🟠

#### 🟦 1. SequencedCollection<E> Interface

- Introduced in Java 21 (Preview)
- Superinterface for ordered collections (like List, Deque, LinkedHashSet, etc.)

###### 🔵Methods

- `E getFirst()`;
- `E getLast()`;
- `void addFirst(E e)`;
- `void addLast(E e)`;
- `E removeFirst()`;
- `E removeLast()`;
- `SequencedCollection<E> reversed()`;

#### 🟦 2. SequencedList<E> Interface

- Extends `List<E>` and `SequencedCollection<E>`
- Meant for lists with a defined order (like ArrayList, LinkedList)
- Inherits all SequencedCollection methods

#### 🟦 3. SequencedSet<E> Interface

- Extends `Set<E>` and `SequencedCollection<E>`
- Ensures no duplicates and maintains order
- Typical implementation: `LinkedHashSet`

### ➡️ Structured Concurrency (Preview):

### ➡️ Vector API (Finalized):

### ➡️ Foreign Function & Memory API (Finalized):

### ➡️ Multi-File Source Launch

### ➡️ String Templates(Preview)
