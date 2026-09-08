# Word Search II

## Problem
Given a character board and a dictionary of words, return all words that can be formed using adjacent cells. A cell cannot be used more than once for one word.

## Intuition
A Trie lets us stop exploring as soon as the current path is not a prefix of any word. Run DFS from every cell while walking through the Trie.

## Java
```java
class Solution {
    static class TrieNode {
        TrieNode[] child = new TrieNode[26];
        String word;
    }

    public List<String> findWords(char[][] board, String[] words) {
        TrieNode root = new TrieNode();
        for (String word : words) {
            TrieNode node = root;
            for (char ch : word.toCharArray()) {
                int i = ch - 'a';
                if (node.child[i] == null) node.child[i] = new TrieNode();
                node = node.child[i];
            }
            node.word = word;
        }

        List<String> ans = new ArrayList<>();
        for (int r = 0; r < board.length; r++) {
            for (int c = 0; c < board[0].length; c++) {
                dfs(board, r, c, root, ans);
            }
        }
        return ans;
    }

    private void dfs(char[][] board, int r, int c, TrieNode node, List<String> ans) {
        if (r < 0 || c < 0 || r >= board.length || c >= board[0].length || board[r][c] == '#') return;
        TrieNode next = node.child[board[r][c] - 'a'];
        if (next == null) return;

        if (next.word != null) {
            ans.add(next.word);
            next.word = null;
        }

        char ch = board[r][c];
        board[r][c] = '#';
        dfs(board, r + 1, c, next, ans);
        dfs(board, r - 1, c, next, ans);
        dfs(board, r, c + 1, next, ans);
        dfs(board, r, c - 1, next, ans);
        board[r][c] = ch;
    }
}
```

## Complexity
Trie construction is O(total characters in words). DFS is bounded by the number of board cells and explored Trie paths; the Trie uses O(total characters) space.