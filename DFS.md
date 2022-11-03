```cpp
#include<bits/stdc++.h>
using namespace std;
void DFS(int node, vector<int>adj[], vector<int>&vis) {
	cout << node << " ";
	vis[node] = 1;
	for(auto it : adj[node]) {
		if(!vis[it])
			DFS(it, adj, vis);
	}
}
int main() {
	int n, m;
	cin >>n >> m;
	vector<int>adj[n + 1];
	int u , v;
	for(int i = 0; i < m; i++) {
		cin >> u >> v;
		adj[u].push_back(v);
		adj[v].push_back(u);
	}
	vector<int>vis(n + 1, 0);
	DFS(1, adj, vis);
}
