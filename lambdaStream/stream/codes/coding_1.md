⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Count even and odd numbers from a list using a single Stream.

```java
import java.util.*;
import java.util.stream.*;

public class EvenOddCount {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1,2,3,4,5,6,7,8,9,10);

        Map<Boolean, Long> result = numbers.stream()
                .collect(Collectors.partitioningBy(n -> n % 2 == 0, Collectors.counting()));

        System.out.println("Even Count: " + result.get(true));
        System.out.println("Odd Count: " + result.get(false));
    }
}

```

- **How it Works**
  - `partitioningBy()` splits the stream into 2 groups:
  - `true` → even numbers
  - `false` → odd numbers
- `counting()` counts items in each bucket.

# ⏺️ Find the Longest Word(s) in a String Using Streams

## Case 1: Get Only One Longest Word

```java
  import java.util.*;
import java.util.stream.*;

public class LongestWord {
    public static void main(String[] args) {
        String sentence = "Java stream API is powerful and interesting";

        String longest = Arrays.stream(sentence.split(" "))
                .max(Comparator.comparingInt(String::length))
                .orElse("");

        System.out.println("Longest Word: " + longest);
    }
}

```

## Case 2: If Multiple Words Have Same Longest Length → Return All

```java
import java.util.*;
import java.util.stream.*;

public class LongestWordsList {
    public static void main(String[] args) {
        String sentence = "Java stream API is powerful and interesting";

        List<String> longestWords = Arrays.stream(sentence.split(" "))
                .collect(Collectors.groupingBy(String::length))
                .entrySet()
                .stream()
                .max(Map.Entry.comparingByKey())
                .map(Map.Entry::getValue)
                .orElse(Collections.emptyList());

        System.out.println("Longest Words: " + longestWords);
    }
}

```

- **How it Works**
  - Split sentence into words using `split(" ")`
  - Group words by length → Map
  - Find max length key
  - Return list of words having that length
