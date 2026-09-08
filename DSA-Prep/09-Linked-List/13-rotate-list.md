# Rotate List

## Intuition
Connect the tail to the head to form a circle, then break it after `n-k` steps from the old head. Reduce k modulo n.

## Java
```java
public ListNode rotateRight(ListNode h,int k){if(h==null||h.next==null)return h;int n=1;ListNode t=h;while(t.next!=null){t=t.next;n++;}k%=n;if(k==0)return h;t.next=h;for(int i=0;i<n-k;i++)t=t.next;ListNode nh=t.next;t.next=null;return nh;}
```

## Complexity
O(n) time, O(1) space.