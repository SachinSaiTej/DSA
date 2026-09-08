# String Compression

## Problem
Compress consecutive repeated characters in place, writing the character followed by its count when the count is greater than one. Return the compressed length.

## Intuition
Use a read pointer to find each run and a write pointer to overwrite the array with the compressed representation.

## Java
```java
public int compress(char[] chars) {
    int read = 0, write = 0;
    while (read < chars.length) {
        char c = chars[read];
        int start = read;
        while (read < chars.length && chars[read] == c) read++;
        chars[write++] = c;
        int count = read - start;
        if (count > 1) {
            for (char digit : String.valueOf(count).toCharArray()) chars[write++] = digit;
        }
    }
    return write;
}
```

## Complexity
Time O(n), space O(1) excluding the temporary count string.