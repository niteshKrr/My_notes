# Binary Search On Answers



## Questions

💡 First try with yourself, if you are unable to solve the question then see the solution.


??? tip "Find square root of a number in log n"


    * <a href="https://www.geeksforgeeks.org/problems/square-root/0?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=square-root" target="_blank">Find square root of a number in log n (gfg)</a>


    ---

    **Always Remember 🥇**

    * The primary **objective** of the **Binary Search** algorithm is to efficiently **determine** the appropriate **half** to eliminate, thereby reducing the **search space** by half. It does this by determining a specific condition that ensures that the **target** is not present in that half.

    * Now, we are **not** given any **sorted array** on which we can apply binary search. But, if we observe closely, we can notice that our answer **space i.e. [1, n]** is sorted. So, we will apply **binary search** on the answer space.


    ---


    ```cpp

    
    #include <bits/stdc++.h>
    using namespace std;

    long long int floorSqrt(long long int x){
        
        long long ans = 1;
        long long low = 1;
        long long high = x;
        while(low <= high){
            
            long long mid = (low + high)/2;
            
            if(mid*mid <= x){
                ans = mid;
                low = mid+1;
            }
            else{
                high = mid-1;
            }
        }
        
        return ans;
    }


    ```

??? tip "Aggressive cows"

    * <a href="https://www.spoj.com/problems/AGGRCOW/" target="_blank">Aggressive cows </a>


    ---

    **Algorithm:**

    * **First**, we will sort the given stalls[] array.

    * **Place the 2 pointers i.e. low and high:** Initially, we will place the pointers. The pointer low will point to 1 and the high will point to (stalls[n-1]-stalls[0]). As the ‘stalls[]’ is sorted, ‘stalls[n-1]’ refers to the maximum, and ‘stalls[0]’ is the minimum element.

    * **Calculate the ‘mid’:** mid = (low+high) / 2 
    
    * **Eliminate the halves based on the boolean value returned by canWePlace():**
    We will pass the potential distance, represented by the variable 'mid', to the **‘canWePlace()'** function. This function will return true if it is possible to place all the cows with a minimum distance of ‘mid’.

        * **If the returned value is true:** On satisfying this condition, we can conclude that the number ‘mid’ is one of our possible answers. But we want the maximum number. So, we will eliminate the left half and consider the right half(i.e. low = mid+1).

        * **Otherwise**, the value mid is greater than the distance we want. This means the numbers greater than ‘mid’ should not be considered and the right half of ‘mid’ consists of such numbers. So, we will eliminate the right half and consider the left half(i.e. high = mid-1).


    ---

    ```cpp



    #include <bits/stdc++.h>
    using namespace std;

    bool canWePlace(vector<int> &stalls, int dist, int cows){
        int n = stalls.size(); //size of array
        int cntCows = 1; //no. of cows placed
        int last = stalls[0]; //position of last placed cow.
        for (int i = 1; i < n; i++) {
            if (stalls[i] - last >= dist) {
                cntCows++; //place next cow.
                last = stalls[i]; //update the last location.
            }
            if (cntCows >= cows) return true;
        }
        return false;
    }
    int aggressiveCows(vector<int> &stalls, int k){
        int n = stalls.size(); //size of array
        //sort the stalls[]:
        sort(stalls.begin(), stalls.end());

        int low = 1, high = stalls[n - 1] - stalls[0];
        int ans = 0;
        //apply binary search:
        while (low <= high) {
            int mid = (low + high) / 2;
            if (canWePlace(stalls, mid, k) == true) {
                ans = mid;
                low = mid + 1;
            }
            else high = mid - 1;
        }
        return ans;
    }

    int main(){

        vector<int> stalls = {0, 3, 4, 7, 10, 9};
        int k = 4;
        int ans = aggressiveCows(stalls, k);
        cout << "The maximum possible minimum distance is: " << ans << "\n";

        return 0;
    }


    ```





??? tip "Book Allocation Problem"

    
    * <a href="https://www.naukri.com/code360/problems/allocate-books_1090540?utm_source=youtube&utm_medium=affiliate&utm_campaign=codestudio_Striver_BinarySeries" target="_blank">Book Allocation Problem (Code 360)</a>


    * <a href="https://leetcode.com/problems/split-array-largest-sum/description/" target="_blank">Split Array Largest Sum (leetcode)</a>

    * <a href="https://www.naukri.com/code360/problems/painter-s-partition-problem_1089557?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf" target="_blank"> Painter's Partition Problem (Code 360)</a>


    ---

    **Algorithm:**

    * **If m > n:** In this case, book allocation is not possible and so, we will return -1.

    * **Place the 2 pointers i.e. low and high:** Initially, we will place the pointers. The pointer low will point to max(arr[]) and the high will point to sum(arr[]).

    * **Calculate the ‘mid’:** mid = (low+high) / 2

    * **Eliminate the halves based on the number of students returned by countStudents():**
    We will pass the potential number of pages, represented by the variable 'mid', to the **‘countStudents()'** function. This function will return the number of students to whom we can allocate the books.

        * **If students > m:** On satisfying this condition, we can conclude that the number ‘mid’ is smaller than our answer. So, we will eliminate the left half and consider the right half(i.e. low = mid+1).

        * **Otherwise,** the value mid is one of the possible answers. But we want the minimum value. So, we will eliminate the right half and consider the left half(i.e. high = mid-1).



    ---

    ```cpp


    #include <bits/stdc++.h>
    using namespace std;

    bool countStudents(vector<int> &arr, int pages , int m) {
        int n = arr.size(); //size of array.
        int students = 1;
        long long sum = 0;
        for (int i = 0; i < n; i++) {
            sum += arr[i];
            if(sum > pages){
                students++;
                sum = arr[i];
            }
        }

        if(students > m){
            return true;
        }
        return false;
    }

    int findPages(vector<int>& arr, int n, int m) {
        //book allocation impossible:
        if (m > n) return -1;

        int low = *max_element(arr.begin(), arr.end());
        int high = accumulate(arr.begin(), arr.end(), 0);

        while (low <= high) {
            int mid = (low + high) / 2;
            if (countStudents(arr, mid , m) == true) {
                low = mid + 1;
            }
            else {
                high = mid - 1;
            }
        }
        return low;
    }

    int main(){

        vector<int> arr = {25, 46, 28, 49, 24};
        int n = 5;
        int m = 4;
        int ans = findPages(arr, n, m);
        cout << "The answer is: " << ans << "\n";

        return 0;
    }



    ```




---

🥇 🥇 🥇


### Other Important Questions List


??? tip "Important Questions List"

    * <a href="https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=find-nth-root-of-m" target="_blank">Find Nth root of M (gfg)</a>



    * <a href="https://leetcode.com/problems/koko-eating-bananas/description/" target="_blank">Koko Eating Bananas (leetcode)</a>


    * <a href="https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/description/" target="_blank">Minimum Number of Days to Make m Bouquets (leetcode)</a>



    * <a href="https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/description/" target="_blank">Find the Smallest Divisor Given a Threshold (leetcode)</a>


    * <a href="https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/" target="_blank">Capacity To Ship Packages Within D Days (leetcode)</a>



    * <a href="https://leetcode.com/problems/kth-missing-positive-number/description/" target="_blank">Kth Missing Positive Number (leetcode)</a>



    * <a href="https://leetcode.com/problems/median-of-two-sorted-arrays/" target="_blank">Median of Two Sorted Arrays (leetcode)</a>


    * <a href="https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=k-th-element-of-two-sorted-array" target="_blank">K-th element of two Arrays (gfg)</a>





💯 🔥 🚀