🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

## ➡️ Can we make a constructor final, static, or abstract? Why/Why not?

- **final:** Constructors can't be inherited, so no point marking them final.
- **static:** Constructors belong to objects, not classes.
- **abstract:** Constructors must have a body to initialize objects.

## ➡️ What will happen if hashCode() is overridden but not equals()?

- Hash-based collections (like HashMap, HashSet) may store duplicates because contract between **hashCode()** and **equals()** is broken.
