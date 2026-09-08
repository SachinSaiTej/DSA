# Design Add and Search Words Data Structure

## Problem
Implement `addWord` and `search`, where `search` supports `.` matching any single character.

## Intuition
A Trie handles normal characters directly. When `.` appears, try every possible child recursively.

## Java
```java
class WordDictionary {
    static class Node {
        Node[] children = new Node[26];
        boolean isWord;
    }

    private final Node root = new Node();

    public void addWord(String word) {
        Node current = root;

        for (char ch : word.toCharArray()) {
            int index = ch - 'a';

            if (current.children[index] == null) {
                current.children[index] = new Node();
            }

            current = current.children[index];
        }

        current.isWord = true;
    }

    public boolean search(String word) {
        return search(root, word, 0);
    }

    private boolean search(Node node, String word, int index) {
        if (node == null) {
            return false;
        }

        if (index == word.length()) {
            return node.isWord;
        }

        char ch = word.charAt(index);

        if (ch == '.') {
            for (Node child : node.children) {
                if (search(child, word, index + 1)) {
                    return true;
                }
            }
            return false;
        }

        return search(node.children[ch - 'a'], word, index + 1);
    }
}
```

## Complexity
Insert O(L). Search is O(26^L) in the worst case with wildcards, where L is the word length.