# I

k短路，dijkstra + A*。本质应该是反向跑一遍dijkstra得到终点到所有点的最短路，然后根据到终点的距离和当前距离正向搜索。