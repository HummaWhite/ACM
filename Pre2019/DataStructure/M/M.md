# M

感觉是个树上分治的问题（比如链剖出来用线段树维护什么的），查了一下发现原来是动态点分治问题。

那么就对着原树建一棵点分树，点分树上的结点维护最小距离，对应原树中点到每层的重心的最小距离。每次把结点$u$改为红色，就在点分树上从$u$到根结点向上更新最小距离：$dis[x] = \min(dis[x], getdist(x, u))$。$getdist(x, u)$是$x$、$u$在原树上的距离，可以用LCA求得。点分树的树深是$\log{n}$级别，LCA也是$\log{n}$，故修改的复杂度为$\log^2{n}$。

查询跟修改差不多，也是在点分树上向上跳转。

总复杂度为：LCA预处理 + 查询：$n\log{n} + m\log^2{n}$