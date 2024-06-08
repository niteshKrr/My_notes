## Questions

💡 First try with yourself, if you are unable to do the question then see the solution.



??? tip "First negative integer in every window of size k"

    * <a href="https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1" target="_blank">First negative integer in every window of size k (gfg)</a>


    ---


    ```cpp

    vector<long long> printFirstNegativeInteger(long long int arr[], long long int N, long long int K) {
                                                 
        vector<long long> ans;
        queue<int> q;
        int i = 0;  
        int j = 0;
        
        while(j < N){
            
            if(arr[j] < 0){
                q.push(arr[j]);
            }
            
            if(j-i+1 < K){
                j++;
            }
            else if(j-i+1 == K){
                
                if(q.empty()){
                    ans.push_back(0);
                }
                else{
                    ans.push_back(q.front());
                }
            
                if(arr[i] < 0){
                    q.pop();
                }
                i++;
                j++;
            }
        }
        
        return ans;
    }


    ```



??? tip "Count Occurences of Anagrams"

    * <a href="https://www.geeksforgeeks.org/problems/count-occurences-of-anagrams5839/1" target="_blank">Count Occurences of Anagrams (gfg)</a>


    ---


    ```cpp
    class Solution{
        public:
        int search(string pat, string txt) {
            
            map<char , int> mp;
            for(int i = 0 ; i < pat.length() ; i++){
                mp[pat[i]]++;
            }
            
            int count = mp.size();
            int k = pat.length();
            int ans = 0;
            int i = 0;
            int j = 0;
            
            while(j < txt.length()){
                
                if(mp.find(txt[j]) != mp.end()){
                    mp[txt[j]]--;
                    if(mp[txt[j]] == 0){
                        count--;
                    }
                }
                if(j-i+1 < k){
                    j++;
                }
                else if(j-i+1 == k){
                    if(count == 0){
                        ans++;
                    }
                    if(mp.find(txt[i]) != mp.end()){
                        mp[txt[i]]++;
                        if(mp[txt[i]] == 1){
                            count++;
                        }
                    }
                    i++;
                    j++;
                }
            }
            return ans;
        }

    };

    ```


??? tip "Maximum of all subarrays of size k"

    * <a href="https://www.geeksforgeeks.org/problems/ipl-2021-match-day-2--141634/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article" target="_blank">Maximum of all subarrays of size k (gfg)</a>


    ---


    ```cpp

    class Solution{
        public:
        vector<int> max_of_subarrays(vector<int> arr, int n, int k) {
            
            vector<int> ans;
            int maxi = INT_MIN;
            int i = 0;
            int j = 0;
            while(j < n){
                
                if(arr[j] > maxi){
                    maxi = arr[j];
                }
                
                if(j-i+1 < k){
                    j++;
                }
                else if(j-i+1 == k){
                    ans.push_back(maxi);
                    if(arr[i] != maxi){
                        i++;
                        j++;
                    }
                    else if(arr[i] == maxi){
                        i++;
                        j = i;
                        maxi = 0;
                    }
                    
                }
            }
            return ans;
        }
    };

    ```


??? tip "Number of subarray whose sum equals to K"


    * <a href="https://leetcode.com/problems/subarray-sum-equals-k/" target="_blank">Subarray Sum Equals K (leetcode)</a>


    ---


    ```cpp

    class Solution {
        public:
        int subarraySum(vector<int>& nums, int k) {
            
            int count = 0;
            int sum = 0;
            map<int,int> mp;

            for(int i = 0 ; i < nums.size() ; i++){
                sum += nums[i];

                if(sum == k){
                    count++;
                }

                if(mp.find(sum-k) != mp.end()){
                    count += mp[sum-k];
                }

                mp[sum]++;
                
            }

            return count;

        }
    };

    ```


??? tip "Number of Substrings Containing All Three Characters"


    * <a href="https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/description/" target="_blank">Number of Substrings Containing All Three Characters (leetcode)</a>

    ---


    **BruteForce**


    ```cpp


    class Solution {
        public:
        int numberOfSubstrings(string s) {
            
            int n = s.length();
            int count = 0;
            for(int i = 0; i < n ; i++){
                vector<int> hash(3,0);
                for(int j = i ; j < n ; j++){
                    hash[s[j]-'a'] = 1;
                    if(hash[0]+hash[1]+hash[2] == 3){
                        count += n-j;
                        break;
                    }
                }
            }
            return count;
        }
    };

    ```

    ---

    **Optimal**


    ```cpp


    class Solution {
        public:
        int numberOfSubstrings(string s) {
            
            vector<int> last_seen(3,-1);
            int ans = 0;
            int j = 0;

            while(j < s.length()){

                last_seen[s[j]-'a'] = j;
                if(last_seen[0] != -1 && last_seen[1] != -1 && last_seen[2] != -1){
                    int mini = min(last_seen[0],min(last_seen[1],last_seen[2]));
                    ans += mini+1;
                }
                j++;
            }
            return ans;
        }
    };

    ```




---

🥇 🥇 🥇


### Other Important Questions List

??? tip "Important Questions List"


    * <a href="https://leetcode.com/problems/longest-substring-without-repeating-characters/description/" target="_blank">Longest Substring Without Repeating Characters (leetcode)</a>


    * <a href="https://leetcode.com/problems/max-consecutive-ones-iii/description/" target="_blank">Max Consecutive Ones III  (leetcode)</a>


    * <a href="https://leetcode.com/problems/longest-repeating-character-replacement/description/" target="_blank">Longest Repeating Character Replacement (leetcode)</a>


    * <a href="https://www.geeksforgeeks.org/problems/fruit-into-baskets-1663137462/1" target="_blank">Fruit Into Baskets (gfg)</a>



    * <a href="https://leetcode.com/problems/binary-subarrays-with-sum/description/" target="_blank">Binary Subarrays With Sum  (leetcode)</a>


    * <a href="https://leetcode.com/problems/count-number-of-nice-subarrays/" target="_blank">Count Number of Nice Subarrays  (leetcode)</a>


    * <a href="https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/description/" target="_blank">Number of Substrings Containing All Three Characters (leetcode)</a>


    * <a href="https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/description/" target="_blank">Maximum Points You Can Obtain from Cards (leetcode)</a>

    



💯 🔥 🚀