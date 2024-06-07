# Sliding Window Technique

## What is Sliding Window Technique?

**Sliding Window** problems are problems in which a **fixed or variable-size window** is moved through a data structure, typically an array or string, to solve problems efficiently based on **continuous** subsets of elements.



**This technique** is commonly used in algorithms like finding **subarrays** with a **specific sum**, finding the **longest substring with unique characters**, or solving problems that require a **fixed-size window** to process elements efficiently.


![loading...](../../images/dsa/sliding_window/Sliding-Window-Technique-copy-(1).webp)


---

## How to use Sliding Window Technique?

There are basically **two** types of sliding window:


### 1. Fixed Size Sliding Window:


The general steps to solve these questions by following below steps:

* Find the size of the window required, say K.
* Compute the result for 1st window.
* Then use a loop to slide the window by 1 and keep computing the result window by window.


??? tip "Max Sum Subarray of size K"

    * <a href="https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1" target="_blank">Max Sum Subarray of size K (gfg)</a>


    ---


    ```cpp

    class Solution{
       public:
        long maximumSumSubarray(int K, vector<int> &arr , int N){
            
            long sum = 0;
            long ans = INT_MIN;
            int i = 0;
            int j = 0;
            
            while(j < N){
                
                sum += arr[j];

                // Compute the result for 1st window.
                if(j-i+1 < K){
                    j++;
                }
                else if(j-i+1 == K){

                    // Slide the window by 1 and keep computing the result window by window.
                    ans = max(ans , sum);
                    sum -= arr[i];
                    i++;
                    j++;
                }
            }
            return ans;
        }
    };


    ```


### 2. Variable Size Sliding Window:


The general steps to solve these questions by following below steps:

* In this type of sliding window problem, we increase our right pointer one by one till our condition is true.
* At any step if our condition does not match, we shrink the size of our window by increasing left pointer.
* Again, when our condition satisfies, we start increasing the right pointer and follow step 1.
* We follow these steps until we reach to the end of the array.


??? tip "Smallest subarray with sum greater than x"

    * <a href="https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article" target="_blank">Smallest subarray with sum greater than x (gfg)</a>


    ---


    ```cpp

    class Solution{
      public:
        int smallestSubWithSum(int arr[], int n, int x){
            
            int sum = 0;
            int ans = INT_MAX;
            int i = 0;
            int j = 0;
            while(j < n){
                
                sum += arr[j];
                while(sum > x){
                    ans = min(ans , j-i+1);
                    sum -= arr[i];
                    i++;
                }
                
                j++;
            }
            
            if(ans == INT_MAX){
                return 0;
            }
            
            return ans;
        }
    };

    ```



## How to Identify Sliding Window Problems:

* These problems generally require Finding Maximum/Minimum **Subarray, Substrings** which satisfy some specific condition.
* The size of the subarray or substring **‘K’** will be given in some of the problems.
* These problems can easily be solved in **O(N^2)** time complexity using nested loops, using sliding window we can solve these in **O(N)** Time Complexity.
* **Required Time Complexity:** O(N) or O(Nlog(N))
* **Constraints:** N <= 10^6 , If N is the size of the Array/String.




