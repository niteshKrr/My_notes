## Depth First Search or DFS

DFS is a traversal technique which involves the idea of recursion and backtracking. DFS goes in-depth, i.e. traverses all nodes by going ahead, and when there are no further nodes to traverse in the current path, then it backtracks on the same path and traverses other unvisited nodes. 

![loading...](../../../images/dsa/graph/graph05.jpg)


---


```cpp

    #include <bits/stdc++.h>
    using namespace std;

    void Helper(vector<int> adj[] , vector<int> &visited , vector<int> &ans , int start){

        visited[start] = 1;
        ans.push_back(start);

        for(auto val : adj[start]){

            if(visited[val] == 0){
                Helper(adj , visited , ans , val);
            }
        }
    }

    vector<int> dfs(vector<int> adj[] , int size){

        vector<int> visited(size , 0);
        int start = 1;
        vector<int> ans;

        Helper(adj , visited , ans , start);

        return ans;
    }

    int main(){

        int V = 6;
        vector<int> adj[V];

        adj[1] = {2, 3};
        adj[2] = {1, 4, 5};
        adj[3] = {1};
        adj[4] = {2};
        adj[5] = {2};

        vector<int> ans = dfs(adj , V);

        for(auto val : ans){
            cout<<val<<" ";
        }

        return 0;
    }

```

#### Time Complexity

For an undirected graph, O(N) + O(2E), For a directed graph, O(N) + O(E), Because for every node we are calling the recursive function once, the time taken is O(N) and 2E is for total degrees as we traverse for all adjacent nodes.

#### Space Complexity

O(3N) ~ O(N), Space for dfs stack space, visited array and an adjacency list.
