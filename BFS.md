```cpp
#include<bits/stdc++.h>
using namespace std;
void BFS(int node, vector<int>adj[], vector<int>&vis) {
	queue<int>q;
	q.push(node);
	vis[node] = 1;
	while(!q.empty()) {
		node = q.front();
		q.pop();
		cout << node << ' ';
		for(auto it : adj[node]) {
			if(!vis[it]) {
				q.push(it);
				vis[it] = 1;
			}
		}
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
	BFS(1, adj, vis);
}
