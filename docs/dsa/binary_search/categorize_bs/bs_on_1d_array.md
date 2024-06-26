# Binary Search On 1D Arrays


## Questions

💡 First try with yourself, if you are unable to solve the question then see the solution.


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

??? tip "Single Element in a Sorted Array"

    * <a href="https://leetcode.com/problems/single-element-in-a-sorted-array/description/" target="_blank">Single Element in a Sorted Array (leetcode)</a>


    ---

    **Resolving edge cases:**

    * **If n == 1**: This means the array size is 1. If the array contains only one element, we will return that element only.
    * **If arr[0] != arr[1]**: This means the very first element of the array is the single element. So, we will return arr[0].
    * **If arr[n-1] != arr[n-2]**: This means the last element of the array is the single element. So, we will return arr[n-1].

    ![loading...](../../../images/dsa/binay_search/single_ele.png)


    * By **observing** the above image, we can clearly notice a striking distinction between the index sequences of the **left** and **right** halves of the single element in the array.

        * The index sequence of the duplicate numbers in the left half is always **(even, odd)**. That means one of the following conditions will be satisfied if we are in the left half.

        * The index sequence of the duplicate numbers in the right half is always (odd, even). That means one of the following conditions will be satisfied if we are in the right half.

    * Now, we can easily identify the left and right halves, just by checking the sequence of the current index, i, like the following:

        * **If (i % 2 == 0 and arr[i] == arr[i+1]) or (i%2 == 1 and arr[i] == arr[i-1])**, we are in the left half.
        * **If (i % 2 == 0 and arr[i] == arr[i-1]) or (i%2 == 1 and arr[i] == arr[i+1])**, we are in the right half.

    * **Note**: In our case, the index i refers to the index ‘mid’.

    * **How to eliminate the halves:**

        * If we are in the left half of the single element, we have to eliminate this left half (i.e. **low = mid+1**). Because our single element appears somewhere on the right side.

        * If we are in the right half of the single element, we have to eliminate this right half (i.e. **high = mid-1**). Because our single element appears somewhere on the left side.


    * Now, we have resolved the problems and we can use the binary search accordingly.


    ---


    ```cpp

    class Solution {
      public:
        int singleNonDuplicate(vector<int>& nums) {
            
            int n = nums.size();
            if(n == 1){
                return nums[0];
            }
            if(nums[0] != nums[1]){
                return nums[0];
            }
            if(nums[n-1] != nums[n-2]){
                return nums[n-1];
            }

            int low = 1;
            int high = n-2;
            while(low <= high){
                int mid = (low + high)/2;
                if(nums[mid] != nums[mid-1] && nums[mid] != nums[mid+1]){
                    return nums[mid];
                }
                else if(mid%2 == 0 && nums[mid] == nums[mid+1] || mid%2 == 1 && nums[mid] == nums[mid-1]){
                    low = mid+1;
                }
                else{
                    high = mid-1;
                }
            }

            return -1;
        }
    };


    ```

??? tip "Find Peak Element"

    * <a href="https://leetcode.com/problems/find-peak-element/" target="_blank">Find Peak Element (leetcode)</a>

    ---

    **What is a peak element?**

    * A peak element in an array refers to the element that is **greater than both of its neighbors**. Basically, if **arr[i]** is the peak element, **arr[i] > arr[i-1] and arr[i] > arr[i+1]**.


    **The steps are as follows:**

    * **If n == 1**: This means the array size is 1. If the array contains only one element, we will return that index i.e. 0.

    * **If arr[0] > arr[1]**: This means the very first element of the array is the peak element. So, we will return the index 0.

    * **If arr[n-1] > arr[n-2]**: This means the last element of the array is the peak element. So, we will return the index n-1.

    * **Place the 2 pointers i.e. low and high**: Initially, we will place the pointers excluding index 0 and n-1 like this: low will point to index 1, and high will point to index n-2 i.e. the second last index.

    * Calculate the **mid**: **mid = (low+high) / 2**

    * **Check if arr[mid] is the peak element:**

        * If **arr[mid] > arr[mid-1] and arr[mid] > arr[mid+1]**: If this condition is true for arr[mid], we can conclude arr[mid] is the peak element. We will return the index **mid**.

        * If **arr[mid] > arr[mid-1]**: This means we are in the left half and we should eliminate it as our peak element appears on the right. So, we will do this :- **low = mid+1**.

        * **Otherwise**, we are in the right half and we should eliminate it as our peak element appears on the left. So, we will do this :- **high = mid-1**.



    ```cpp

    class Solution {
       public:
        int findPeakElement(vector<int>& nums) {
            
            int n = nums.size();
            if(n == 1){
                return 0;
            }
            if(nums[0] > nums[1]){
                return 0;
            }
            if(nums[n-1] > nums[n-2]){
                return n-1;
            }

            int low = 1;
            int high = n-2;
            while(low <= high){
                int mid = (low + high)/2;
                if(nums[mid] > nums[mid-1] && nums[mid] > nums[mid+1]){
                    return mid;
                }
                else if(nums[mid] > nums[mid-1]){
                    low = mid+1;
                }
                else{
                    high = mid-1;
                }
            }

            return -1;
        }
    };


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


    ---

    * <a href="https://leetcode.com/problems/search-in-rotated-sorted-array/description/" target="_blank">Search in Rotated Sorted Array (leetcode)</a>


    **The steps are as follows:**

    * Check **if arr[mid] == target** :- If it is, return the index mid.

    * Identify the sorted half, check where the target is located, and then eliminate one half accordingly:

        * If **arr[low] <= arr[mid]**: This condition ensures that the left part is sorted

            * If **arr[low] <= target && target <= arr[mid]**: It signifies that the target is in this sorted half. So, we will eliminate the right half **(high = mid-1)**.
            * **Otherwise**, the target does not exist in the sorted half. So, we will eliminate this left half by doing **low = mid+1**.
        * **Otherwise, if the right half is sorted**:
            * If **arr[mid] <= target && target <= arr[high]**: It signifies that the target is in this sorted right half. So, we will eliminate the left half **(low = mid+1)**.
            * **Otherwise**, the target does not exist in this sorted half. So, we will eliminate this right half by doing **high = mid-1**.


    ---


    * <a href="https://leetcode.com/problems/search-in-rotated-sorted-array-ii/description/" target="_blank">Search in Rotated Sorted Array II (leetcode)</a>


    * However, in the current problem, the array may contain **duplicates**. Consequently, **the previous approach will not work when arr[low] = arr[mid] = arr[high]**.

    * Hence in the **previous** question **add** check if **arr[low] = arr[mid] = arr[high]**: If this condition is satisfied, we will just increment the low pointer and decrement the high pointer by one step. We will not perform the later steps until this condition is no longer satisfied. So, we will continue to the next iteration from this step.

    * And rest are as same as previous one.


    ---

    * <a href="https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/" target="_blank">Find Minimum in Rotated Sorted Array (leetcode)</a>


    **The steps are as follows:**

    * Place the 2 pointers i.e. **low and high**

    * Calculate the **mid**: **mid = (low+high) / 2**

    * Identify the sorted half, and after picking the leftmost element, eliminate that half.

        * If **arr[low] <= arr[mid]**: This condition ensures that the left part is sorted. So, we will pick the leftmost element i.e. **arr[low]**. Now, we will compare it with 'ans' and update 'ans' with the smaller value (i.e., **min(ans, arr[low])**). Now, we will eliminate this left half(i.e. **low = mid+1**).

        * **Otherwise, if the right half is sorted**:  This condition ensures that the right half is sorted. So, we will pick the leftmost element i.e. **arr[mid]**. Now, we will compare it with 'ans' and update 'ans' with the smaller value (i.e., **min(ans, arr[mid])**). Now, we will eliminate this right half(i.e. **high = mid-1**).

    * This process will be inside a loop and the loop will continue until low crosses high. Finally, we will return the ‘ans’ variable that stores the minimum element.


    ---


    * <a href="https://www.geeksforgeeks.org/problems/rotation4723/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=rotation" target="_blank">Find out how many times has an array been rotated (gfg)</a>




💯 🔥 🚀
