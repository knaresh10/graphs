# Dijsktra's algorithm

*Dijkstra's algorithm is an algorithm for finding the shortest paths between nodes in a graph, which may represent, for example, road networks. It was conceived by computer scientist Edsger W. Dijkstra in 1956 and published three years later.*

```cpp
// dijkstra's algorithm is used to find the shortest path from source node to all other nodes 
#include<bits/stdc++.h>
#define ll long long
using namespace std;
void Dijkstra(vector<pair<int, int>> adj[], int n, int src) {
	// pq is a min heap used to store {dist, node} where dist is distance of node from src
	priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
	vector<int> dist(n, 1e9);
	vector<int> path(n , -1);
	dist[src] = 0;
	pq.push({0, src});
	while (!pq.empty()) {
		int dis = pq.top().first;
		int node = pq.top().second;
		pq.pop();
		for (auto it : adj[node]) {
			int u = it.first;
			int wt = it.second;
			if (dis + wt < dist[u]) {
				path[u] = node;
				dist[u] = dis + wt;
				pq.push({dist[u], u});
			}
		}
	}
	for (auto it : path) cout << it << ' ';
	cout << endl;
	for (auto it : dist) cout << it << " ";
}
int main() {
	int n, m;
	cin >> n >> m;
	vector<pair<int, int >> adj[n];
	for (int i = 0; i < m; i++) {
		int u, v, wt;
		cin >> u >> v >> wt;
		adj[u].push_back({v, wt});
		adj[v].push_back({u, wt});
	}
	
	int src;
	cin >> src;
	Dijkstra(adj, n, src);
}
```

![image](https://user-images.githubusercontent.com/82667769/217436327-4c603b2c-b05c-4240-ad4c-be3af7a317e8.png)

## Input

```cpp
9 14
0 1 4
0 7 8
1 2 8
1 7 11
2 3 7
2 8 2
2 5 4
3 4 9
3 5 11
4 5 10
5 6 2
6 7 1
6 8 6
7 8 7
0
```

![image](https://user-images.githubusercontent.com/82667769/217436381-2c7aa29b-4ee0-4240-85a5-3c2ac6546fa0.png)

## Output

```cpp
-1 0 1 2 5 6 7 0 2 
0 4 12 19 21 11 9 8 14 
```

