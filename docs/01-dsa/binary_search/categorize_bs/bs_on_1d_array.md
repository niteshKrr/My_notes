# Binary Search On 1D Arrays


## Questions

💡 First try with yourself, if you are unable to do the question then see the solution.


* Both **Lower Bound** and **Upper Bound** is very important. 🥇 🥇


??? tip "Implement Lower Bound"


    ---

    **What is Lower Bound?**

    * The lower bound algorithm finds the **first or the smallest index** in a sorted array where the **value** at that index is greater than or equal to a given key i.e. x.

    * The lower bound is the smallest index, ind, where arr[ind] >= x. But **if any such index is not found**, the lower bound algorithm returns n i.e. size of the given array.



    ---


    ```cpp

    
    #include <bits/stdc++.h>
    using namespace std;

    int lowerBound(vector<int> arr, int n, int x) {
        int low = 0, high = n - 1;
        int ans = n;

        while (low <= high) {
            int mid = (low + high) / 2;
            // maybe an answer
            if (arr[mid] >= x) {
                ans = mid;
                //look for smaller index on the left
                high = mid - 1;
            }
            else {
                low = mid + 1; // look on the right
            }
        }
        return ans;
    }

    int main(){

        vector<int> arr = {3, 5, 8, 15, 19};
        int n = 5, x = 9;
        int ind = lowerBound(arr, n, x);
        cout << "The lower bound is the index: " << ind << "\n";

        return 0;
    }


    ```


??? tip "Implement Upper Bound"


    ---

    **What is Upper Bound?**

    * The upper bound algorithm finds the first or the smallest index in a sorted array where the value at that index is greater than the given key i.e. x.

    * The upper bound is the smallest index, where arr[ind] > x.

    * But **if any such index is not found**, the upper bound algorithm returns n i.e. size of the given array. The main **difference between** the lower and upper bound is in the condition. **For the lower bound the condition was arr[ind] >= x** and here, **in the case of the upper bound, it is arr[ind] > x**.



    ---


    ```cpp

    #include <bits/stdc++.h>
    using namespace std;

    int upperBound(vector<int> &arr, int x, int n) {
        int low = 0, high = n - 1;
        int ans = n;

        while (low <= high) {
            int mid = (low + high) / 2;
            // maybe an answer
            if (arr[mid] > x) {
                ans = mid;
                //look for smaller index on the left
                high = mid - 1;
            }
            else {
                low = mid + 1; // look on the right
            }
        }
        return ans;
    }

    int main(){

        vector<int> arr = {3, 5, 8, 9, 15, 19};
        int n = 6, x = 9;
        int ind = upperBound(arr, x, n);
        cout << "The upper bound is the index: " << ind << "\n";

        return 0;
    }


    ```



---

🥇 🥇 🥇


### Other Important Questions List


??? tip "Important Questions List"

    * <a href="https://leetcode.com/problems/binary-search/description/" target="_blank">Binary Search (leetcode)</a>


    * <a href="https://www.geeksforgeeks.org/problems/floor-in-a-sorted-array-1587115620/1?track=DSASP-Searching&amp%253BbatchId=154&utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=floor-in-a-sorted-array" target="_blank">Floor in a Sorted Array (gfg)</a>


    * <a href="https://www.geeksforgeeks.org/problems/ceil-the-floor2802/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=ceil-the-floor" target="_blank">Ceil The Floor (gfg)</a>


    * <a href="https://leetcode.com/problems/search-insert-position/description/" target="_blank">Search Insert Position (leetcode)</a>


    * <a href="https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/" target="_blank">Find First and Last Position of Element in Sorted Array (leetcode)</a>



    * <a href="https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=number-of-occurrence" target="_blank">Number of occurrence (gfg)</a>

