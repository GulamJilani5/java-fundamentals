# Primitive Types

- Java has exactly 8 primitives
- Primitives are not objects → No methods, no null (except if boxed).
- Default values in class fields:
  - Numeric → 0
  - boolean → false
  - char → '\u0000' (null character)

| Type        | Size (bits)                                                | Range / Description                                 |
| ----------- | ---------------------------------------------------------- | --------------------------------------------------- |
| **byte**    | 8                                                          | -128 to 127                                         |
| **short**   | 16                                                         | -32,768 to 32,767                                   |
| **int**     | 32                                                         | -2³¹ to 2³¹-1 (\~ -2.1B to +2.1B)                   |
| **long**    | 64                                                         | -2⁶³ to 2⁶³-1 (very large integers)                 |
| **float**   | 32                                                         | \~6–7 decimal digits precision (IEEE 754)           |
| **double**  | 64                                                         | \~15–16 decimal digits precision (IEEE 754)         |
| **char**    | 16                                                         | Single Unicode character (`'\u0000'` to `'\uffff'`) |
| **boolean** | JVM-dependent (usually 1 bit, stored as 1 byte internally) | `true` or `false`                                   |

# Wrapper Classes (Object versions of primitives)

- These are objects in java.lang that wrap primitive values. They allow primitives to be treated like objects (e.g., in Collections).
- Can be used in Collections (like List<Integer>) because Collections work only with objects, not primitives.
- Support null values (primitives cannot be null).

| Primitive | Wrapper Class |
| --------- | ------------- |
| `byte`    | `Byte`        |
| `short`   | `Short`       |
| `int`     | `Integer`     |
| `long`    | `Long`        |
| `float`   | `Float`       |
| `double`  | `Double`      |
| `char`    | `Character`   |
| `boolean` | `Boolean`     |
