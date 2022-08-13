<!--yml
category: codewars
date: 2022-08-13 11:42:18
-->

# 【Codewars C++ 3kyu】: Path Finder #3: the Alpinist_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547889?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-100547889-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_36362028/article/details/100547889?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-100547889-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 问题描述:

## Task

You are at start location `[0, 0]` in mountain area of NxN and you can **only** move in one of the four cardinal directions (i.e. North, East, South, West). Return minimal number of `climb rounds` to target location `[N-1, N-1]`. Number of `climb rounds` between adjacent locations is defined as difference of location altitudes (ascending or descending).

Location altitude is defined as an integer number (0-9).

## Path Finder Series:

# 代码实现：

```
#include <cmath>
#include <queue>
// solve the shortest path --> Dijkstra algorithm
int V; // real nums of vertices
const int NUM = 50000;  // set the maximum nums of vertices is 50000
int go[4][2] = {
    0, 1,
    1, 0,
    0, -1,
    -1, 0
};

struct node{ 
    int next, c; 
    bool operator<(const node &o) const{
        return c > o.c;
    }
}; 

int dijkstra(std::vector<node> edge[NUM], int src) { 
    std::priority_queue<node> Q; 
    std::vector<int>dist(V, -1);
    dist[src] = 0; 
    node tmp;
    tmp.next = src;
    tmp.c = dist[src];
    Q.push(tmp);

    while ( !Q.empty() ) { 
        tmp = Q.top();
        Q.pop();
        int u = tmp.next;
        if ( u == V - 1 ) return dist[u];
        for (int i = 0; i < edge[u].size(); i++) {
            int v = edge[u][i].next;
            int c = edge[u][i].c;
            if (dist[v] == -1 || dist[u] + c < dist[v]){
                dist[v] = dist[u] + c; 
                tmp.c = dist[v], tmp.next = v;
                Q.push(tmp);
            }
        }
     } 
     return dist[V - 1];
}

int path_finder(std::string maze) {
    int length = std::floor( std::sqrt( (double) maze.size() ) );
    std::cout << length << std::endl;
    V = length * length;
    std::vector<node> edge[NUM];
    for ( int i = 0; i < V; i++ ) edge[i].clear();
    for ( int x = 0; x < length; x++ ) {
        for ( int y = 0; y < length; y++ ) {
            for ( int i = 0; i < 4; i++ ) {
                int nx = x + go[i][0];
                int ny = y + go[i][1];
                if ( nx < 0 || nx >= length || ny < 0 || ny >= length ) continue;
                node tmp;
                tmp.next = nx * length + ny;
                tmp.c = std::abs(maze[nx * ( length + 1 )+ ny] - maze[x * ( length + 1 ) + y]);
                edge[x * length + y].push_back(tmp);
            }
        }
    }

    int src = 0;
    return dijkstra(edge, src); 
}
```