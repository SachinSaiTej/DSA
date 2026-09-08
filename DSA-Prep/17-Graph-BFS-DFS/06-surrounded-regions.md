# Surrounded Regions

## Problem
Capture every region of `O` completely surrounded by `X`; border-connected `O` cells remain unchanged.

## Intuition
Only border-connected regions can survive. Mark those cells temporarily, flip remaining `O` to `X`, then restore the marks.

## Java
```java
public void solve(char[][] b){
    int R=b.length,C=b[0].length;
    for(int r=0;r<R;r++){mark(b,r,0);mark(b,r,C-1);}
    for(int c=0;c<C;c++){mark(b,0,c);mark(b,R-1,c);}
    for(int r=0;r<R;r++)for(int c=0;c<C;c++)if(b[r][c]=='O')b[r][c]='X';else if(b[r][c]=='#')b[r][c]='O';
}
void mark(char[][]b,int r,int c){if(r<0||c<0||r==b.length||c==b[0].length||b[r][c]!='O')return;b[r][c]='#';mark(b,r+1,c);mark(b,r-1,c);mark(b,r,c+1);mark(b,r,c-1);}
```

## Complexity
Time O(RC), space O(RC) worst case.