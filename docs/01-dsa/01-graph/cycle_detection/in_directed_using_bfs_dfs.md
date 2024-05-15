## Detect Cycle in an directed Graph using BFS

#### Intuition:

1. Since we know topological sorting is only possible for directed acyclic graphs(DAGs) if we apply Kahn’s algorithm in a directed cyclic graph(A directed graph that contains a cycle), it will fail to find the topological sorting(i.e. The final sorting will not contain all the nodes or vertices).

2. So, finally, we will check the sorting to see if it contains all V vertices or not. If the result does not include all V vertices, we can conclude that there is a cycle.


![loading...](../../../images/dsa/graph/graph13.png)

---


```cpp

// Function to detect cycle in a directed graph.
bool isCyclic(int V, vector<int> adj[]) {
	int indegree[V] = {0};
	for (int i = 0; i < V; i++) {
		for (auto it : adj[i]) {
			indegree[it]++;
		}
	}

	queue<int> q;
	for (int i = 0; i < V; i++) {
		if (indegree[i] == 0) {
			q.push(i);
		}
	}

	int cnt = 0;
	// o(v + e)
	while (!q.empty()) {
		int node = q.front();
		q.pop();
		cnt++;
		// node is in your topo sort
		// so please remove it from the indegree

		for (auto it : adj[node]) {
			indegree[it]--;
			if (indegree[it] == 0) q.push(it);
		}
	}

	if (cnt == V) return false;
	return true;
}

```

#### Time Complexity

O(V+E), where V = no. of nodes and E = no. of edges. This is a simple BFS algorithm.

#### Space Complexity

O(N) + O(N) ~ O(2N), O(N) for the in-degree array, and O(N) for the queue data structure used in BFS(where N = no.of nodes).



---

## Detect Cycle in an directed Graph using DFS


![loading...](../../../images/dsa/graph/graph14.png)


!!! success "Only we have do"

    We need to create an extra **`dfs_visited[n]`** array to keep track of visited nodes in the current path.



```cpp

bool dfs_recursive_cyclic(vector<int> adj_list[], int n, bool visited[], bool dfs_visited[], int node){
  visited[node]=true;
  dfs_visited[node]=true;

  for(auto&e:adj_list[node]){
    if(visited[e]==false){
      bool return_val = dfs_recursive_cyclic(adj_list, n, visited, dfs_visited,e);
      if(return_val==true)return true;
    }
    else if(dfs_visited[e]==true){
      return true;
    }
  }
  dfs_visited[node]=false;
  return false;
}

int detectCycleInDirectedGraph(int n, vector < pair < int, int >> & edges) {
  // Write your code here.
  vector<int> adj_list[n+1];
  for(auto &e:edges){
    int x= e.first;
    int y= e.second;
    adj_list[x].push_back(y);
  }

  bool visited[n+1]={false};

  for(int i=0;i<n;i++){
    if(visited[i]==true)continue;
    bool dfs_visited[n+1]={false};
    bool return_val = dfs_recursive_cyclic(adj_list, n+1, visited, dfs_visited,i);
    if(return_val==true)return true;
  }
  return false;

}


```
