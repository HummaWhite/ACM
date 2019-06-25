# N

就是在很简单的朴素走迷宫上加了个向左右走的最大步数限制。

必须bfs

这就改变了上下与左右的对称关系，由于上下随便走没有影响，我们可以直接从左到右把图分成一层一层，然后每次把一层中能到的位置全部加入队列（按层扩展），可以保证消耗次数少的先搜到。

这需要特别注意打vis标记的顺序，否则可能一不小心$O(mn)$就变成了$O(k^n)$