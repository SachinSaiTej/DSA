# Clone Graph

## Problem
Deep-copy an undirected connected graph.

## Intuition
Use DFS with a map from original node to clone. Put a node in the map before visiting neighbors to handle cycles.

## Java
```java
public Node cloneGraph(Node node) {
    if (node == null) return null;
    Map<Node, Node> map = new HashMap<>();
    return dfs(node, map);
}
private Node dfs(Node n, Map<Node,Node> map) {
    if (map.containsKey(n)) return map.get(n);
    Node copy = new Node(n.val);
    map.put(n, copy);
    for (Node nei : n.neighbors) copy.neighbors.add(dfs(nei, map));
    return copy;
}
```

## Complexity
Time O(V + E), space O(V).