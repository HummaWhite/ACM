# J

> O me da se，终于等到连通性状压dp了

这道题的状态很容易想到，就只令$f[i][j]$为处理到第$i$行，当前连通性为$j$时所需要清除最少的垃圾个数。转移时枚举上一行状态$k$，如果$k$到$j$合法，$f[i, j] = \min(f[i, j], f[i-1, k] + cost(j))$，$cost(j)$为把这一行变成$j$需要清除垃圾的个数。

最多只有8列4种不同的连通块，所以可以8位5进制数+最小表示法（不用最小表示法的话总数有$5^8=390625$种，会T）。然后预处理所有合法的最小表示法串。发现$n=8$时应该是$836$种（要注意$01020102$这种交叉连通不存在的状态）。接着处理每一行原有状态可以变成哪些状态。

然后就是前一行的最小表示法到后一行的最小表示法之间转移的合法性判断了……具体只能代码表述了。卡好久才想出来，写了个可以跳的dfs……巨丑（而且之前还常数巨大T了）。这个应该是最麻烦的地方吧。后面dp就没什么了。

在开始dp前还可以优化一下，即头尾两端略过全是1的行。

这还是最简单的连通性状压dp……还没有插头轮廓线之类更复杂的东西……