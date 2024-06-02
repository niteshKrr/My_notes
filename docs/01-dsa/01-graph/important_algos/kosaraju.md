## Strongly Connected Components - Kosaraju's Algorithm

A component is called a Strongly Connected Component(SCC) only if for every possible pair of vertices (u, v) inside that component, u is reachable from v and v is reachable from u.

* Strongly Connected Components are only valid for directed graph.

**In the below directed graph, the Strongly Connected Component(SCC) have been marked**

![loading...](../../../images/dsa/graph/kosaraju.png)


* To find the strongly connected components of a given directed graph, we uses Kosaraju’s Algorithm.


* **we can expect two types of questions from this topic :-**
    * Find the number of strongly connected components of a given graph.
    * Print the strongly connected components of a given graph.


---

???+ tip "Steps to perform Kosaraju’s Algorithm"

    * Sort all the nodes according to their finishing time, to do this we did topological sort using DFS.
    * Reverse all the edges of the entire graph.
    * Perform the DFS and count the no. of different DFS calls to get the no. of SCC.


### Code

```cpp

    #include <bits/stdc++.h>
    using namespace std;

    class Solution
    {
      private:
        void dfs(int node, vector<int> &vis, vector<int> adj[], stack<int> &st) {
            vis[node] = 1;
            for (auto it : adj[node]) {
                if (!vis[it]) {
                    dfs(it, vis, adj, st);
                }
            }

            st.push(node);
        }
     private:
        void dfs3(int node, vector<int> &vis, vector<int> adjT[]) {
            vis[node] = 1;
            for (auto it : adjT[node]) {
                if (!vis[it]) {
                    dfs3(it, vis, adjT);
                }
            }
        }
     public:
        //Function to find number of strongly connected components in the graph.
        int kosaraju(int V, vector<int> adj[])
        {
            vector<int> vis(V, 0);
            stack<int> st;
            for (int i = 0; i < V; i++) {
                if (!vis[i]) {
                    dfs(i, vis, adj, st);
                }
            }

            vector<int> adjT[V];
            for (int i = 0; i < V; i++) {
                vis[i] = 0;
                for (auto it : adj[i]) {
                    // i -> it
                    // it -> i
                    adjT[it].push_back(i);
                }
            }

            int scc = 0;
            while (!st.empty()) {
                int node = st.top();
                st.pop();
                if (!vis[node]) {
                    scc++;
                    dfs3(node, vis, adjT);
                }
            }
            return scc;
        }
    };


```

---

#### Time Complexity

O(V+E) + O(V+E) + O(V+E) ~ O(V+E) , where V = no. of vertices, E = no. of edges. The first step is a simple DFS, so the first term is O(V+E). The second step of reversing the graph and the third step, containing DFS again, will take O(V+E) each.

#### Space Complexity
O(V)+O(V)+O(V+E), where V = no. of vertices, E = no. of edges. Two O(V) for the visited array and the stack we have used. O(V+E) space for the reversed adjacent list.


