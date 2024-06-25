# Questions

💡 First try with yourself, if you are unable to do the question then see the solution.



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






---

🥇 🥇 🥇


### Other Important Questions List

??? tip "Important Questions List"


    * <a href="https://www.geeksforgeeks.org/problems/does-array-represent-heap4345/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=does-array-represent-heap">Does array represent Heap (gfg)</a>



    * <a href="https://leetcode.com/problems/kth-largest-element-in-an-array/description/">Kth Largest Element in an Array (leetcode)</a>



    * <a href="https://www.geeksforgeeks.org/problems/kth-smallest-element5635/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=kth-smallest-element">Kth Smallest (gfg)</a>




    



💯 🔥 🚀