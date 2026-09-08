# Sudoku Solver

## Problem
Fill a 9×9 Sudoku board so every row, column, and 3×3 box contains digits 1–9 exactly once.

## Intuition
Find an empty cell and try each valid digit. If a choice eventually causes failure, undo it and try the next digit.

## Java
```java
public void solveSudoku(char[][]b){solve(b);}
boolean solve(char[][]b){for(int r=0;r<9;r++)for(int c=0;c<9;c++)if(b[r][c]=='.'){for(char x='1';x<='9';x++)if(valid(b,r,c,x)){b[r][c]=x;if(solve(b))return true;b[r][c]='.';}return false;}return true;}
boolean valid(char[][]b,int r,int c,char x){for(int i=0;i<9;i++)if(b[r][i]==x||b[i][c]==x||b[r/3*3+i/3][c/3*3+i%3]==x)return false;return true;}
```

## Complexity
Worst-case exponential; recursion depth O(81).