# About findNeedles documentation

This API reference document explains how to call the findNeedles() method. There are many variations of the findNeedles() method on the internet, but I have decided to document this version as I believe the developer can improve the code.

## Audience

This document is intended for experienced Java programmers.

## Suggestions for the developer

- We should consider removing the limit on the number of needles. Currently, it is limited to 5, but we should allow users to use any number of needles.
- We should consider moving the initialization of the 'words' string array outside the first for loop.

  **Existing logic**
  ```java
  for (int i = 0; i < needles.length; i++) { 
      String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0); 
      for (int j = 0; j < words.length; j++) { 
          if (words[j].compareTo(needles[i]) == 0) { 
              countArray[i]++; 
          } 
      } 
  }
  ```
  **Improved logic**
  ```java
  String[] words = haystack.split("[ \"\'\t\n\b\f\r]", 0);
  for (int i = 0; i < needles.length; i++) {
     for (int j = 0; j < words.length; j++) {
         if (words[j].compareTo(needles[i]) == 0) {
             countArray[i]++;
         }
     }
  }
  ```

In the existing logic, the split method for the haystack string is executed for every iteration of the first 'for' loop. This is not required as the 'words' string array is reassigned with the same value whenever it is inside the 'for' loop. The improved logic shows that it is better if the 'words' string array is assigned only once. Hence, we should move the string array outside the first for loop. This improves the program's speed, especially when the haystack is big.