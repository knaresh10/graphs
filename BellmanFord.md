# Bellman Ford Algorithm

*Bellman Ford Algorithm is a dynamic programming algorithm that solves the single source shortest path problem for a graph with negative edge weights. It is slower than Dijkstra's algorithm for the same problem, but more versatile, as it is capable of handling graphs in which some of the edge weights are negative numbers.*

```cpp
// BellmanFord algorithm is used to find the shortest path from source to all nodes
//  it used in DIRECTED GRAPH and it can be used even when graphs has negative edges
//  it is used to detect the negative edges
#include<bits/stdc++.h>
#define ll long long
using namespace std;
void bellmanFord(int V, vector<vector<int>>& edges, int S) {
	vector<int> dist(V, 1e8);
	dist[S] = 0;

	// the algorithm runs for V - 1 types to relax all the edges
	for (int i = 1; i < V; i++) {
		for (auto it : edges) {
			if (dist[it[0]] + it[2] < dist[it[1]]) {
				dist[it[1]] = dist[it[0]] + it[2];
			}
		}
	}

	//  to detect the negative cycle we once more run the algorithm for Vth time 
	// since negative cycle leads to decrease in the dist we can find the whether negative edge is present or not
	for (auto it : edges) {
		if (dist[it[0]] + it[2] < dist[it[1]]) {
			cout << "Negative Cycle";
			return ;
		}
	}

	for (auto it : dist) cout << it << " ";
}
int main() {
	int n, m;
	cin >> n >> m;
	vector<vector<int>> edges;
	for (int i = 0; i < m; i++) {
		int u, v, wt; cin >> u >> v >> wt;
		edges.push_back({u, v, wt});
	}
	int src;
	cin >> src;
	bellmanFord(n, edges, src);
}
```
## Input

```cpp
3 4
0 1 5
1 0 3
1 2 -1
2 0 1
2
```

## Output

```cpp
1 6 0 
```

## Input

```cpp
4 7
0 1 -3
0 3 -10
1 3 3
2 0 7
2 3 -1
3 0 9
3 1 -4
0
```

## Output

```cpp
Negative Cycle
```
