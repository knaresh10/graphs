```cpp
#include<bits/stdc++.h>
using namespace std;
int main() {
	int n, m;
	cin >>n >> m;
	vector<vector<int>>mat(n + 1, vector<int>(n + 1, 0));
	int u , v;
	for(int i = 0; i < m; i++) {
		cin >> u >> v;
		mat[u][v] = 1;
		mat[v][u] = 1;
	}
}
