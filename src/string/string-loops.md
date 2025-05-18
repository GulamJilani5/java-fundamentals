🔴🔵☑️✔️ ➡️ ✓→•←⁕⁂※⁜‣

# Different ways to loop over the string

### ➡️1) Using a for Loop with charAt()
     String str = "Hello";
     for (int i = 0; i < str.length(); i++) {
         char ch = str.charAt(i);
         System.out.println("Character at index " + i + ": " + ch);
     }

### ➡️2) Using a for Loop with toCharArray()
    String str = "Hello";
    char[] chars = str.toCharArray();
    for (int i = 0; i < chars.length; i++) {
        System.out.println("Character at index " + i + ": " + chars[i]);
    }

 ### ➡️3) Using an Enhanced for Loop with toCharArray()
       String str = "Hello";
       for (char ch : str.toCharArray()) {
           System.out.println("Character: " + ch);
       }

 ### ➡️4) Using String.split() and an Enhanced for Loop
    String str = "Hello";
    for (String ch : str.split("")) {
        System.out.println("Character: " + ch);
    }

 ### ➡️5) Using Stream with chars()
      String str = "Hello";
      str.chars()
         .mapToObj(ch -> (char) ch)
         .forEach(ch -> System.out.println("Character: " + ch));

 ### ➡️6) Using Stream with codePoints()
     String str = "Hello";
     str.codePoints()
        .mapToObj(ch -> (char) ch)
        .forEach(ch -> System.out.println("Character: " + ch));

 ### ➡️7) Using a While Loop with charAt()
    String str = "Hello";
    int i = 0;
    while (i < str.length()) {
        char ch = str.charAt(i);
        System.out.println("Character at index " + i + ": " + ch);
        i++;
    }

### ➡️8) Using StringCharacterIterator
       import java.text.StringCharacterIterator;
       String str = "Hello";
       StringCharacterIterator iterator = new StringCharacterIterator(str);
       for (char ch = iterator.first(); ch != StringCharacterIterator.DONE; ch = iterator.next()) {
           System.out.println("Character: " + ch);
       }




