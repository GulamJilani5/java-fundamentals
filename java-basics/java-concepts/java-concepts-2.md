⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️

## ➡️ Private members(fields/methods)

- private variable/method can be accessed only inside the same class.
- If another class wants access private fields, we must expose it using public/protected/default getters/setters.
  - Now any class (same package or different package) can access using getters/setters.

## ➡️ Static methods/variables access

- static members can be accessed using ClassName.member from any class.
- But Access also depends on access modifier:
  - `private static` → only same class
  - `default static` → same package
  - `protected static` → same package + subclass outside package
  - `public static` → everywhere

## ➡️ Access Modifiers are only 4

- private
- default (package-private) (no keyword)
- protected
- public

#### 🟦 Cannot combine access modifiers

- private public String name; WRONG

## ➡️ Non-access modifiers

- final
- static
- abstract
- synchronized
- volatile
- transient
- native
- strictfp
