# Questions

💡 First try with yourself, if you are unable to solve the question then see the solution.



??? tip "Convert Min Heap to Max Heap"

    * <a href="https://www.geeksforgeeks.org/problems/convert-min-heap-to-max-heap-1666385109/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=convert-min-heap-to-max-heap">Convert Min Heap to Max Heap (gfg)</a>


    ---

    ```cpp

    class Solution{
        public:
        void heapify(vector<int> &arr , int N , int i){
            
            int large = i;
            int left = 2*i+1;
            int right = 2*i+2;
            
            if(left < N && arr[left] > arr[large]){
                large = left;
            }
            if(right < N && arr[right] > arr[large]){
                large = right;
            }
            
            if(large != i){
                swap(arr[large],arr[i]);
                heapify(arr,N,large);
            }
        }

        void convertMinToMaxHeap(vector<int> &arr, int N){
            
            for(int i = N/2-1 ; i >= 0 ; i--){
                heapify(arr,N,i);
            }
                
        }
        
    };


    ```


??? tip "Task Scheduler"

    * <a href="https://leetcode.com/problems/task-scheduler/description/">Task Scheduler (leetcode)</a>


    ---

    ```cpp

    class Solution {
        public:
        int leastInterval(vector<char>& tasks, int n) {
            
            map<char,int> mp;
            for(auto it : tasks){
                mp[it]++;
            }

            priority_queue<int> pq;
            for(auto it : mp){
                pq.push(it.second);
            }

            int ans = 0;
            while(!pq.empty()){

                vector<int> rem;
                for(int i = 1 ; i <= n+1 ; i++){
                    if(!pq.empty()){
                        rem.push_back(pq.top()-1);
                        pq.pop();
                    }
                }

                for(auto it : rem){
                    if(it > 0){
                        pq.push(it);
                    }
                }

                if(pq.empty()){
                    // only zeros are present in the "rem" vector.
                    ans += rem.size();
                }
                else{
                    ans += n+1;
                }
            }
            return ans;
        }
    };

    ```


??? tip "Maximum Sum Combinations"

    * <a href="https://www.interviewbit.com/problems/maximum-sum-combinations/">Task Scheduler (interviewbit)</a>


    ---

    **Bruteforce**

    ```cpp

    vector<int> Solution::solve(vector<int> &A, vector<int> &B, int C) {
    
        priority_queue<int> pq;
        vector<int> ans;
        int n = A.size();
        int m = B.size();
        
        for(int i = 0 ; i < n ; i++){
            
            for(int j = 0 ; j < m ; j++){
                int sum = A[i]+B[j];
                pq.push(sum);
            }
        }
        
        while(C > 0){
            ans.push_back(pq.top());
            pq.pop();
            C--;
        }
        
        return ans;
    }


    ```

    ---

    **Optimal**

    ```cpp

    vector<int> Solution::solve(vector<int> &A, vector<int> &B, int C) {
        
        priority_queue<int, vector<int>, greater<int>> pq;
        sort(A.begin(), A.end(), greater<int>());
        sort(B.begin(), B.end(), greater<int>());
        int N = A.size();

        for(int i=0; i<C; i++){
            pq.push(A[i] + B[i]);
        }

        vector<int> ans(C);
        for(int i=0; i<N; i++){
            for(int j=0; j<N; j++){
                if(i==j)
                    continue;
                if(A[i] + B[j] > pq.top())
                {
                    pq.pop();
                    pq.push(A[i] + B[j]);
                }
                else
                    break;
            }
        }
        for(int i=C-1; i>=0; i--){
            ans[i] = pq.top();
            pq.pop();
        }
        return ans;
    }


    ```


??? tip "Design Twitter"


    * <a href="https://leetcode.com/problems/design-twitter/description/">Design Twitter (leetcode)</a>


    ---


    ```cpp

    class Twitter {
    public:

        map<int,set<int>> friends;
        priority_queue<vector<int>> tweets;
        int cnt = 0;

        Twitter() {

        }
        
        void postTweet(int userId, int tweetId) {
            tweets.push({cnt++,tweetId,userId});
        }
        
        vector<int> getNewsFeed(int userId) {
            vector<int>ans;
            priority_queue<vector<int>>userFeed = tweets;
            int n = 0;
            while(!userFeed.empty() && n < 10){
                auto topTweet = userFeed.top(); // tweetId, userId
                userFeed.pop();
                if(topTweet[2] == userId || friends[userId].count(topTweet[2])){
                    ans.push_back(topTweet[1]);
                    n++;
                }
            }
            return ans;
        }
        
        void follow(int followerId, int followeeId) {
            friends[followerId].insert(followeeId);
        }
        
        void unfollow(int followerId, int followeeId) {
            friends[followerId].erase(followeeId);
        }
    };


    ```







---

🥇 🥇 🥇


### Other Important Questions List

??? tip "Important Questions List"


    * <a href="https://www.geeksforgeeks.org/problems/does-array-represent-heap4345/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=does-array-represent-heap">Does array represent Heap (gfg)</a>



    * <a href="https://leetcode.com/problems/kth-largest-element-in-an-array/description/">Kth Largest Element in an Array (leetcode)</a>



    * <a href="https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=kth-smallest-element">Kth Smallest (gfg)</a>



    * <a href="https://www.geeksforgeeks.org/problems/merge-k-sorted-arrays/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=merge-k-sorted-arrays">Merge k Sorted Arrays (gfg)</a>



    * <a href="https://leetcode.com/problems/merge-k-sorted-lists/">Merge k Sorted Lists (leetcode)</a>



    * <a href="https://www.geeksforgeeks.org/problems/replace-elements-by-its-rank-in-the-array/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=replace-elements-by-its-rank-in-the-array">Replace elements by its rank in the array (gfg)</a>



    * <a href="https://leetcode.com/problems/hand-of-straights/">Hand of Straights (leetcode)</a>



    * <a href="https://leetcode.com/problems/kth-largest-element-in-a-stream/description/">Kth Largest Element in a Stream (leetcode)</a>



    * <a href="https://leetcode.com/problems/top-k-frequent-elements/description/">Top K Frequent Elements (leetcode)</a>



    * <a href="https://leetcode.com/problems/find-median-from-data-stream/description/">Find Median from Data Stream (leetcode)</a>





    



💯 🔥 🚀