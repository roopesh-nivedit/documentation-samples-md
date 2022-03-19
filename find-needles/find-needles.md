# findNeedles

Compares five needles with a haystack and displays the number of times a needle appears in the haystack.

```java
public static void findNeedles(String haystack, String[] needles)
```

## Parameters

| Name | Data Type | Description |
|------|-----------|-------------|
| haystack | String | A string containing one or more words. The string can contain spaces and Java escape sequences. For example, "I saw a blue bird and a blue animal".<br><br>The haystack supports the following Java escape sequences:<br>- \\" <br>- \t <br>- \n <br>- \b <br>- \f <br>- \r|
| needles | String[] | An array of five string values. Example: { "I", "saw", "two", "blue", "birds" }. |

## Definition

The following is the definition of the `findNeedles()` method.

```java
public static void findNeedles(String haystack, String[] needles) {
    if (needles.length > 5) {
        System.err.println("Too many words!");
}
else {
    int[] countArray = new int[needles.length];
    for (int i = 0; i < needles.length; i++) {
        // The haystack is split into words based on delimiters.
        String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
        for (int j = 0; j < words.length; j++) {
            if (words[j].compareTo(needles[i]) == 0) {
                countArray[i]++;
            }
        }
    }
    for (int j = 0; j < needles.length; j++) {
        System.out.println(needles[j] + ": " + countArray[j]);
        }
    }
}
```

## Example

The following is a snippet that you can use as an example to call the `findNeedles()` method.

```java
String haystack = "I saw a blue bird and a blue animal";
String[] needles = {"I","saw","two","blue","birds"};

findNeedles(haystack, needles);
```

The following is a sample output for the values specified in the above snippet.

```
I: 1
saw: 1
two: 0
blue: 2
birds: 0
```

## Limitations

The following are the limitations of the `findNeedles()` method:

- The haystack does not support the backslash Java escape sequence (\\\\).
- The comparison with the haystack is limited to five needles only.