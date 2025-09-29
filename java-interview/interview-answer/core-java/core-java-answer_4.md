🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

## ➡️ 2. Explain String immutability. Why are String objects immutable?

##### 🟦 Why are Strings Immutable in Java?

This is one of the most commonly asked interview questions - and for good reason! Strings are special in Java, and their immutability is a design choice that makes the language more secure and efficient.

- Here's why

##### 🟦 Security

- Imagine if database URLs, usernames, or passwords stored as Strings could be modified by another class
- It would be a big risk.

##### 🟦 Caching & Performance

The hashcode of a String is cached once created. Since Strings never change, lookups in HashMap/ HashSet are blazing fast.

##### 🟦 Thread-Safety

- Multiple threads can safely use the same String without worrying about synchronization.
- Enables String Constant Pool.
- Since Strings can't change, they can be stored and reused from a special memory area (SCP), saving huge memory.

##### 🟦 In short:

- Immutability = Security + Performance + Reusability
- I'll cover String Constant Pool in the next post, and how it ties directly to immutability
