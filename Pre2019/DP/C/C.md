# C



> “いいよ、来いよ！打在Bug上！Bug上！！！”（指初始化的边界条件）

玩梗归玩梗，下面正经地讲述题解。

题目的意思是求抽出k个手办然后保持原来的先后关系插回去所得到的最小连通块个数。转换一下就是选出n-k个，然后按照原来的先后顺序排成一排，再把剩下的k个随意插进序列得到的最小混乱值。可以分成两个阶段做，而两个阶段的联系就是高度：把k个手办中的某一个插回去时，如果前面n-k个中没有这种高度的，答案+1。这就需要知道第一阶段选了哪些高度。我们注意到h的取值是114514~114521这8种情况，那么就可以状压维护一个高度集合S。

$dp[i][j][last][S]$表示当前第$i$个，选了$j$个手办且最后选的高度为$k$时，所有选过的手办的高度集合为$S$时的最小混乱度。

第一阶段：取和不取两种选择，对应转移方程

取：$dp[i+1, j+1, A_{i+1}, S | A_{i+1}] = \min(dp[i, j, last, S]+(A_{i+1}==last ? 0 : 1))$

不取：$dp[i+1, j, last, S] = \min(dp[i, j, last, S])$

第二个阶段我们枚举已经取了n-k个时的所有高度情况，即$ans = \min(dp[n, n-k, last, S] + cntBit(S xor U))$，U为n个手办的高度集合。

```C++
for (int s = 1; s <= n; s++)
		dp[s][1][a[s]][1<<a[s]] = 1;  //就这个初始化没写好WA了好几次……
```

