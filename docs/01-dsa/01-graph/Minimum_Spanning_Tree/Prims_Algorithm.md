## Prim's Algorithm - Minimum Spanning Tree

Prim's algorithm is a minimum spanning tree algorithm that takes a graph as input and finds the subset of the edges of that graph which

* form a tree that includes every vertex.
* has the minimum sum of weights among all the trees that can be formed from the graph

???+ tip "The steps for implementing Prim's algorithm"
    1. Initialize the minimum spanning tree with a vertex chosen at random.
    2. Find all the edges that connect the tree to new vertices, find the minimum and add it to the tree.
    3. Keep repeating step 2 until we get a minimum spanning tree.


---

```cpp

class Solution{
public:
	//Function to find sum of weights of edges of the Minimum Spanning Tree.
	int spanningTree(int V, vector<vector<int>> adj[]){

		priority_queue<pair<int, int>,vector<pair<int, int> >, greater<pair<int, int>>> pq;
		vector<int> vis(V, 0);
		// {wt, node}
		pq.push({0, 0});
		int sum = 0;
		while (!pq.empty()) {
			auto it = pq.top();
			pq.pop();
			int node = it.second;
			int wt = it.first;

			if (vis[node] == 1) continue;
			// add it to the mst
			vis[node] = 1;
			sum += wt;
			for (auto it : adj[node]) {
				int adjNode = it[0];
				int edW = it[1];
				if (!vis[adjNode]) {
					pq.push({edW, adjNode});
				}
			}
		}
		return sum;
	}
};


```

---

#### Time Complexity

O(E*logE) + O(E*logE)~ O(E*logE), where E = no. of given edges.<br>
-> The maximum size of the priority queue can be E so after at most E iterations the priority queue will be empty and the loop will end. Inside the loop, there is a pop operation that will take logE time. This will result in the first O(E*logE) time complexity. Now, inside that loop, for every node, we need to traverse all its adjacent nodes where the number of nodes can be at most E. If we find any node unvisited, we will perform a push operation and for that, we need a logE time complexity. So this will result in the second O(E*logE).

#### Space Complexity

O(E) + O(V), where E = no. of edges and V = no. of vertices.

