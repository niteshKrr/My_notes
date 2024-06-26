# Binary Search On 2D Arrays


## Questions

💡 First try with yourself, if you are unable to solve the question then see the solution.


??? tip "Row with max 1s"


    * <a href="https://www.geeksforgeeks.org/problems/row-with-max-1s0023/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=row-with-max-1s" target="_blank">Row with max 1s (gfg)</a>


    ---

    ```cpp

    class Solution{
        public:
        int lower_bound(vector<int> &arr , int n , int k){
            
            int low = 0;
            int high = n-1;
            int ans = n;
            while(low <= high){
                int mid = (low + high)/2;
                if(arr[mid] >= k){
                    ans = mid;
                    high = mid-1;
                }
                else{
                    low = mid+1;
                }
            }
            return ans;
        }

        int rowWithMax1s(vector<vector<int> > arr, int n, int m) {
            
            int ans = -1;
            int maxi = 0;
            
            for(int i = 0 ; i < n ; i++){
                
                int cnt_1 = m - lower_bound(arr[i] , m , 1);
                if(cnt_1 > maxi){
                    maxi = cnt_1;
                    ans = i;
                }
            }
            
            return ans;
        }

    };


    ```



??? tip "Find a Peak Element II"


    * <a href="https://leetcode.com/problems/find-a-peak-element-ii/description/" target="_blank">Find a Peak Element II (leetcode)</a>

    ---

    ```cpp

    class Solution {
        public:
        int solver(vector<vector<int>>& mat , int col){
            int maxi = 0;
            int ans = 0;
            for(int i = 0 ; i < mat.size() ; i++){
                if(mat[i][col] > maxi){
                    maxi = mat[i][col];
                    ans = i;
                }
            }
            return ans;
        }

        vector<int> findPeakGrid(vector<vector<int>>& mat) {
            
            int low = 0;
            int high = mat[0].size()-1;
            
            while(low <= high){
                int mid = (low+high)/2;
                int max_ele_row = solver(mat , mid);
                int left = mid-1 >= 0 ? mat[max_ele_row][mid-1] : -1;
                int right = mid+1 < mat[0].size() ? mat[max_ele_row][mid+1] : -1;

                if(mat[max_ele_row][mid] > left && mat[max_ele_row][mid] > right){
                    return {max_ele_row,mid};
                }
                else if(left > mat[max_ele_row][mid]){
                    high = mid-1;
                }
                else{
                    low = mid+1;
                }
            }
            return {-1,-1};
        }
    };

    ```



??? tip "Median in a row-wise sorted Matrix"


    * <a href="https://www.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=median-in-a-row-wise-sorted-matrix" target="_blank">Median in a row-wise sorted Matrix (leetcode)</a>

    ---

    * For video take a look of **take_u_forward** channel.

    ---


    ```cpp

    class Solution{
        public:
        int upperBound(vector<int> &arr, int x, int n) {
            int low = 0, high = n - 1;
            int ans = n;
        
            while (low <= high) {
                int mid = (low + high) / 2;
                if (arr[mid] > x) {
                    ans = mid;
                    high = mid - 1;
                }
                else {
                    low = mid + 1;
                }
            }
            return ans;
        }
        
        int countSmallEqual(vector<vector<int>> &matrix, int m, int n, int x) {
            int cnt = 0;
            for (int i = 0; i < n; i++) {
                cnt += upperBound(matrix[i], x, m);
            }
            return cnt;
        }

        int median(vector<vector<int>> &matrix, int R, int C){
            
            int low = INT_MAX, high = INT_MIN;
            int m = matrix[0].size();
            int n = matrix.size();

            for (int i = 0; i < n; i++) {
                low = min(low, matrix[i][0]);
                high = max(high, matrix[i][m - 1]);
            }
        
            int req = (n * m) / 2;
            while (low <= high) {
                int mid = (low + high) / 2;
                int smallEqual = countSmallEqual(matrix, m, n, mid);
                if (smallEqual <= req) low = mid + 1;
                else high = mid - 1;
            }
            return low;
        }
    };


    ```





---

🥇 🥇 🥇


### Other Important Questions List


??? tip "Important Questions List"


    * <a href="https://leetcode.com/problems/search-a-2d-matrix/description/" target="_blank">Search a 2D Matrix (leetcode)</a>


    * <a href="https://leetcode.com/problems/search-a-2d-matrix-ii/description/" target="_blank">Search a 2D Matrix II (leetcode)</a>


    * <a href="https://www.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=median-in-a-row-wise-sorted-matrix" target="_blank">Median in a row-wise sorted Matrix (gfg)</a>






💯 🔥 🚀