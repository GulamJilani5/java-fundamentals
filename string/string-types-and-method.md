🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

### ➡️

# Different Methods In Different Types Of String

### ➡️ 1)String Literal(Immutable) & String Object(Immutable) :

##### String Literal

- Stored in String Constant Pool.
- If the same literal already exists, it reuses it.
- preferred for memory efficiency

##### String Object

- Stored in heap memory outside the String pool.
- Creates a new object, even if the same value exists.

### 🔵 String Literal's Methods

##### charAt(int index)\*

- Returns the character at the specified index.

##### codePointAt(int index)\*

- Returns the Unicode code point at the specified index.

##### codePointBefore(int index)\*

- Returns the Unicode code point before the specified index.

##### codePointCount(int beginIndex, int endIndex)\*

- Returns the number of Unicode code points in the range.

##### compareTo(String anotherString)☑️

- Compares two strings lexicographically.

##### compareToIgnoreCase(String str)

- Compares two strings lexicographically, ignoring case.

##### concat(String str)☑️

- Concatenates the specified string to the end.

##### contains(CharSequence s)☑️

- Checks if the string contains the specified sequence.

##### contentEquals(CharSequence cs)☑️

- Compares the string to a CharSequence for equality.

##### contentEquals(StringBuffer sb)

- Compares the string to a StringBuffer for equality.

##### endsWith(String suffix)☑️

- Checks if the string ends with the specified suffix.

##### equals(Object anObject)☑️

- Compares the string with another object for equality.

##### equalsIgnoreCase(String anotherString)

- Compares strings, ignoring case.

##### formatted(Object... args)

- Formats the string using the specified arguments (Java 15+).

##### getBytes()

- Encodes the string into a byte array using the default charset.

##### getBytes(Charset charset)

- Encodes the string into a byte array using the specified charset.

##### getBytes(String charsetName)

- Encodes the string into a byte array using the named charset.

##### getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)\*

- Copies characters to a char array.

##### indexOf(int ch)\*☑️

- Returns the index of the first occurrence of the specified character.

##### indexOf(int ch, int fromIndex)\*

- Returns the index of the first occurrence of the character, starting from fromIndex.

##### indexOf(String str)\*

- Returns the index of the first occurrence of the specified substring.

##### indexOf(String str, int fromIndex)\*

- Returns the index of the first occurrence of the substring, starting from fromIndex.

##### intern()

- Returns a canonical representation from the String Pool.

##### isBlank()☑️

- Checks if the string is empty or contains only whitespace (Java 11+).

##### isEmpty()☑️

- Checks if the string is empty.

##### lastIndexOf(int ch)\*☑️

- Returns the index of the last occurrence of the specified character.

##### lastIndexOf(int ch, int fromIndex)\*

- Returns the index of the last occurrence of the character, starting backward from fromIndex.

##### lastIndexOf(String str)\*

- Returns the index of the last occurrence of the specified substring.

##### lastIndexOf(String str, int fromIndex)\*

- Returns the index of the last occurrence of the substring, starting backward from fromIndex.

##### length()\*☑️

- Returns the length of the string.

##### lines()

- Returns a stream of lines split by line terminators (Java 11+).

##### matches(String regex)

- Checks if the string matches the specified regex.

##### offsetByCodePoints(int index, int codePointOffset)\*

- Returns the index offset by the specified number of code points.

##### regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len)

- Tests if two string regions are equal, with optional case insensitivity.

##### regionMatches(int toffset, String other, int ooffset, int len)

- Tests if two string regions are equal.

##### repeat(int count)☑️

- Repeats the string the specified number of times (Java 11+).

##### replace(char oldChar, char newChar)☑️

- Replaces all occurrences of oldChar with newChar.

##### replace(CharSequence target, CharSequence replacement)

- Replaces all occurrences of target with replacement.

##### replaceAll(String regex, String replacement)

- Replaces all substrings matching the regex with replacement.

##### replaceFirst(String regex, String replacement)

- Replaces the first substring matching the regex with replacement.

##### •split(String regex)

- Splits the string into an array based on the regex.

##### •split(String regex, int limit)

- Splits the string with a limit on the number of splits.

##### •startsWith(String prefix)☑️

- Checks if the string starts with the specified prefix.

##### •startsWith(String prefix, int toffset)

- Checks if the string starts with the prefix at the specified offset.

##### •strip()

- Removes leading and trailing whitespace (Unicode-aware, Java 11+).

##### •stripIndent()

- Removes incidental whitespace from multiline strings (Java 15+).

##### •stripLeading()

- Removes leading whitespace (Java 11+).

##### •stripTrailing()

- Removes trailing whitespace (Java 11+).

##### substring(int beginIndex)\* ☑️

- Returns a substring from beginIndex to the end. substring() is very closest to **slice()** in js.

##### •substring(int beginIndex, int endIndex)\*

- Returns a substring from beginIndex to endIndex - 1.

##### •toCharArray()☑️

- Converts the string to a character array.

##### •toLowerCase()

- Converts the string to lowercase.

##### •toLowerCase(Locale locale)

- Converts the string to lowercase using the specified locale.

##### •toString()\*

- Returns the string itself.

##### •toUpperCase()

- Converts the string to uppercase.

##### •toUpperCase(Locale locale)

- Converts the string to uppercase using the specified locale.

##### •transform(Function<String, R> f)

- Applies a function to the string (Java 12+).

##### •translateEscapes()

- Translates escape sequences in the string (Java 15+).

##### •trim()

- Removes leading and trailing whitespace.

##### •valueOf(boolean b)

- Converts a boolean to a string (static).

##### •valueOf(char c)

- Converts a char to a string (static).

##### •valueOf(char[] data)

- Converts a char array to a string (static).

##### •valueOf(char[] data, int offset, int count)

- Converts a portion of a char array to a string (static).

##### •valueOf(double d)

- Converts a double to a string (static).

##### •valueOf(float f)

- Converts a float to a string (static).

##### •valueOf(int i)

- Converts an int to a string (static).

##### •valueOf(long l)

- Converts a long to a string (static).

##### •valueOf(Object obj)

- Converts an object to a string (static).

##### •describeConstable()

- Returns an Optional<String> for constant description (Java 12+).

##### •resolveConstantDesc(MethodHandles.Lookup lookup)

- Resolves the string as a constant (Java 12+).
  •Common Methods: 14 methods marked with (\*) are shared with StringBuilder and StringBuffer: charAt(), codePointAt(), codePointBefore(), codePointCount(), getChars(), indexOf() (all variants), lastIndexOf() (all variants), length(), offsetByCodePoints(), substring() (both variants), toString().
  •Total: ~70 methods (including overloads and static methods).
  •These methods are exclusive to the String class and work identically for both literals and objects.
  •Since String is immutable, methods like replace() or toUpperCase() return a new String rather than modifying the original.

### ➡️ 2) StringBuilder (Mutable)

        •Not thread-safe, so it's faster than StringBuffer.
        •A mutable sequence of characters, designed for efficient string manipulation,
         especially in loops or when appending frequently.

### 🔵 StringBuilder Methods:

##### • Append

##### • append()

##### • appendCodePoint(int codePoint)

          – Appends a Unicode code point.

##### • capacity()

           – Returns the current capacity.

##### • charAt(int index)\*

            – Returns the character at the specified index.

##### • codePointAt(int index)\*

            – Returns the Unicode code point at the specified index.

##### • codePointBefore(int index)\*

            – Returns the Unicode code point before the specified index.

##### • codePointCount(int beginIndex, int endIndex)\*

            – Returns the number of Unicode code points in the ran

##### • delete(int start, int end)

            – Removes characters from start to end - 1.

##### • deleteCharAt(int index)

            – Removes the character at the specified index.

##### • ensureCapacity(int minimumCapacity)

            – Ensures the capacity is at least the specified value.

##### • getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)\*

            – Copies characters to a char array.

##### • indexOf(String str)\*

            – Returns the index of the first occurrence of str.

##### • lastIndexOf(String str)\*

            – Returns the index of the last occurrence of str.

##### • lastIndexOf(String str, int fromIndex)\*

            – Returns the index of the last occurrence of str starting backward from fromIndex.

##### • offsetByCodePoints(int index, int codePointOffset)\*

            – Returns the index offset by the specified number of code points.

##### • replace(int start, int end, String str)

            – Replaces characters from start to end - 1 with str.

##### • reverse()

            – Reverses the sequence of characters.

##### • setCharAt(int index, char ch)

            – Sets the character at the specified index.

##### • setLength(int newLength)

            – Sets the length (truncates or pads with null characters).

##### • substring(int start)\*

            – Returns a substring from start to the end (as a String).

##### • substring(int start, int end)\*

            – Returns a substring from start to end - 1 (as a String).

##### • toString()\*

            – Converts the StringBuilder to a String.

##### • trimToSize()

            – Reduces the capacity to the current length.

• Common Methods: 14 methods marked with (\*) are shared with String and StringBuffer: charAt(),
codePointAt(), codePointBefore(), codePointCount(), getChars(), indexOf() (both variants), lastIndexOf()
(both variants), length(), offsetByCodePoints(), substring() (both variants), toString().

### ➡️ 3) StringBuffer (Mutable)

      -thread-safe, making it suitable for multi-threaded environments.
      -Slightly slower than StringBuilder due to synchronization overhead.

### 🔵 StringBuffer methods:

##### • append()

##### • capacity()

            – Returns the current capacity.

##### • charAt(int index)\*

            – Returns the character at the specified index.

##### • codePointAt(int index)\*

            – Returns the Unicode code point at the specified index.

##### • codePointBefore(int index)\*

            – Returns the Unicode code point before the specified index.

##### • codePointCount(int beginIndex, int endIndex)\*

            – Returns the number of Unicode code points in the range.

##### • delete(int start, int end)

            – Removes characters from start to end - 1.

##### • deleteCharAt(int index)

            – Removes the character at the specified index.

##### • ensureCapacity(int minimumCapacity)

            – Ensures the capacity is at least the specified value.

##### • getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)\*

            – Copies characters to a char array.

##### • indexOf()

##### • insert()

##### • lastIndexOf(String str)\*

            – Returns the index of the last occurrence of str.

##### • lastIndexOf(String str, int fromIndex)\*

            – Returns the index of the last occurrence of str starting backward from fromIndex.

##### • offsetByCodePoints(int index, int codePointOffset)\*

            – Returns the index offset by the specified number of code points.

##### • replace(int start, int end, String str)

            – Replaces characters from start to end - 1 with str.

##### • reverse()

            – Reverses the sequence of characters.

##### • setCharAt(int index, char ch)

            – Sets the character at the specified index.

##### • setLength(int newLength)

            – Sets the length (truncates or pads with null characters).

##### • substring()\*

##### • toString()\*

##### • trimToSize()

            – Reduces the capacity to the current length.

• Common Methods: 14 methods marked with (\*) are shared with String and StringBuilder: charAt(),
codePointAt(), codePointBefore(), codePointCount(), getChars(), indexOf() (both variants),
lastIndexOf() (both variants), length(), offsetByCodePoints(), substring() (both variants), toString().

### 🔵 14 Methods Common To String, StringBuilder, and StringBuffer are:

###### •charAt(int index)

###### •codePointAt(int index)

###### •codePointBefore(int index)

###### •codePointCount(int beginIndex, int endIndex)

###### •getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)

###### •indexOf(String str)

###### •indexOf(String str, int fromIndex)

###### •lastIndexOf(String str)

###### •lastIndexOf(String str, int fromIndex)

###### •length()

###### •offsetByCodePoints(int index, int codePointOffset)

###### •substring(int start)

###### •substring(int start, int end)

###### •toString()

### These methods are implemented in each class, but their behavior reflects the class’s nature:

### String: Immutable, so substring() returns a new String.

### StringBuilder/StringBuffer: Mutable, so charAt() and length() reflect the current state, but substring() still

### returns a String.
