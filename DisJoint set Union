# Disjoint Set Union

```cpp
#include<bits/stdc++.h>
using namespace std;
vector<int> r, parent;

// setData is used to initialize the parent and rank of each node in the graph
void setData(int n) {
	for (int i = 0; i <= n; i++) {
		parent.push_back(i);
		r.push_back(0);
	}
}

// findParent is used to find the parent of a node
int findParent(int u) {
	if (u == parent[u])
		return u;
	return parent[u] = findParent(parent[u]);
}

// Union is used to merge two nodes
void Union(int u, int v) {
	u = findParent(u);
	v = findParent(v);
	// if the rank of u is greater than v then v becomes the parent of u
	if (r[u] > r[v])
		parent[v] = u;

	// if the rank of v is greater than u then u becomes the parent of v
	else if (r[v] > r[u])
		parent[u] = v;
	
	// if the rank of u and v is same then any one of them can be the parent and the rank of the parent is increased by 1
	else {
		parent[u] = v;
		r[u]++;
	}
}
int main() {
	int n, m;
	// cin >> n >> m
	setData(7);
	Union(1, 2);
	Union(2, 3);
	Union(4, 5);
	Union(6, 7);
	Union(5, 6);

	cout << (findParent(3) == findParent(7));

	Union(3, 7);

	cout << (findParent(3) == findParent(7));
}
```
