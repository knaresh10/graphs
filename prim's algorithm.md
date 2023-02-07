# Prim's Algorithm

```cpp
#include<bits/stdc++.h>
#define ll long long
using namespace std;
void prims(vector<pair<int, int>> adj[], int n) {
	// store the sum
	int sum = 0;

	// to store the edges of MST
	vector<pair<int, int>> edges;

	// to store visited vertices
	vector<int> vis(n, 0);

	// to store the {wt, node, parent} in min - heap
	priority_queue<vector<int>, vector<vector<int>>, greater<vector<int>>> pq;
	pq.push({0, 0, -1});
	while (!pq.empty()) {
		auto it = pq.top();
		pq.pop();
		int wt = it[0];
		int node = it[1];
		int parent = it[2];

		// for first node we will add all the adjacent nodes into the priority queue
		if (parent == -1) {
			vis[node] = 1;
			sum += wt;
			for (auto it : adj[node])
				//  add the adjacent nodes only if they are not visited
				if (vis[it.first] == 0)
					pq.push({it.second, it.first, node});
		} else {
			//  for other nodes
			//  we will first check if the node is not visited then only we will check it's neighbours
			if (vis[node] == 0) {
				vis[node] = 1;
				edges.push_back({parent, node});
				sum += wt;
				for (auto it : adj[node]) {
					if (vis[it.first] == 0)
						pq.push({it.second, it.first, node});
				}
			}
		}
	}
	for (auto it : edges) cout << it.first << " " << it.second << endl;
	cout << sum;
}
int main() {
	int n, m;
	cin >> n >> m;
	vector<pair<int, int>> adj[n];
	for (int i = 0; i < m; i++) {
		int u, v, wt;
		cin >> u >> v >> wt;
		adj[u].push_back({v, wt});
		adj[v].push_back({u, wt});
	}

	prims(adj, n);
}

```

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
```

## Output

```cpp
0 1
1 2
2 8
2 5
5 6
6 7
2 3
3 4
37
```
