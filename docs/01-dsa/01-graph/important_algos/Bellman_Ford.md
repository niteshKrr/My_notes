## Bellman Ford Algorithm

Bellman-Ford is a single source shortest path algorithm that determines the shortest path between a given source vertex and every other vertex in a graph. This algorithm can be used on both weighted and unweighted graphs.

* This algorithm is only applicable for **directed graphs**.


![loading...](../../../images/dsa/graph/Bellman-Ford-Algorithm.jpg)


!!! tip

    A **Bellman-Ford algorithm** is also guaranteed to find the shortest path in a graph, similar to **Dijkstra’s algorithm**. Although Bellman-Ford is **slower** than Dijkstra’s algorithm, it is capable of handling graphs with **negative edge weights**, which makes it more **versatile**.


## Idea 🤔

- The Bellman-Ford algorithm’s primary principle is that it starts with a single source and calculates the distance to each node.

- The distance is initially unknown and assumed to be infinite, but as time goes on, the algorithm relaxes those paths by identifying a few shorter paths.

- Hence it is said that Bellman-Ford is based on **`Principle of Relaxation`**.

- Iterate through all the edges for **(n-1) times**, do relaxation.
- To detect cycle, iterate for the one last time **(n time)**, and if a single relaxation is possible, means the graph contains negative cycles, and hence shortest distance can't be found.

---

## What is relaxation in Bellman-ford algorithm?

```cpp
// dist[] <= distance of nodes from a source node
// if there's an edge from x to y, and the dist can be reduced, do it.
// this is called relaxation.
if (dist[x]+wt < dist[y]){
    dist[y]=dist[x]+wt;
}

```

## Why iterate for **(n-1) times**?

- In the worst case, for a graph with **n nodes**, the farthest node from source node can be at the **(n-1 edge)** (if they are in one component).
- So, if we have iterated for (n-1) times and did the relaxation, we can be sure that we have covered the worst case. Now, either some nodes will be in another component (which can't be visited from source node), or a negative cycle will be present in the graph.

![loading...](../../../images/dsa/graph/bellman-ford-worst-case.png)

- If the other nodes are in another component, then again no updation in the distance array will happen.
- But, if the graph have negative cycle, our distance array will again be updated (in other words, relaxation condition will be true).

![loading...](../../../images/dsa/graph/negative-cycle.png)

- So, when we are iterating through all the edges for the **nth time**, a single relaxation condition is sufficient to indicate the graph contains **negative cycle**.

---

### Code

```cpp

//  Function to implement Bellman Ford
//  edges: vector of vectors which represents the graph
//  S: source vertex to start traversing graph with
//  V: number of vertices

vector<int> bellman_ford(int V, vector<vector<int>>& edges, int S) {
	vector<int> dist(V, 1e8);
	dist[S] = 0;
	for (int i = 0; i < V - 1; i++) {
		for (auto it : edges) {
			int u = it[0];
			int v = it[1];
			int wt = it[2];
			if (dist[u] != 1e8 && dist[u] + wt < dist[v]) {
				dist[v] = dist[u] + wt;
			}
		}
	}
	// Nth relaxation to check negative cycle
	for (auto it : edges) {
		int u = it[0];
		int v = it[1];
		int wt = it[2];
		if (dist[u] != 1e8 && dist[u] + wt < dist[v]) {
			return { -1};
		}
	}

	return dist;
}


```


#### Time Complexity 

O(V*E), where V = no. of vertices and E = no. of Edges.

#### Space Complexity

O(V) for the distance array which stores the minimized distances.
