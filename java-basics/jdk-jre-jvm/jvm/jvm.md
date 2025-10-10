# JVM

- JVM divides memory into runtime data areas:
- The core engine that runs Java bytecode.
- Think of it as the **"interpreter"** that takes compiled Java bytecode (`.class files`) and executes it on your machine.
- Platform-dependent implementation, but bytecode is platform-independent.

### JVM Memory Areas

| Memory Area                         | Purpose                                                       | When Used                |
| ----------------------------------- | ------------------------------------------------------------- | ------------------------ |
| **Method Area (a.k.a. Class Area)** | Stores class metadata, static variables, method bytecode      | When class is **loaded** |
| **Heap**                            | Stores **objects** and their instance variables               | When you use `new`       |
| **Stack**                           | Stores local variables, method call frames                    | When methods are invoked |
| **PC Register**                     | Stores the current executing instruction address for a thread | Internal                 |
| **Native Method Stack**             | Used for native (non-Java) code                               | If JNI is used           |
