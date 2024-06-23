# Questions

💡 First try with yourself, if you are unable to do the question then see the solution.



??? tip "Lowest Common Ancestor of a Binary Search Tree"

    * <a href="https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/" target="_blank">Lowest Common Ancestor of a Binary Search Tree (leetcode)</a>


    ---


    ```cpp

    class Solution {
        public:
        TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
            
            if(root == NULL){
                return NULL;
            }

            if(p ->val < root ->val && q ->val < root ->val){
                return lowestCommonAncestor(root ->left , p , q);
            }
            else if(p ->val > root ->val && q ->val > root ->val){
                return lowestCommonAncestor(root ->right , p , q);
            }
            else{
                return root;
            }
        }
    };

    ```




---

🥇 🥇 🥇


### Other Important Questions List

??? tip "Important Questions List"


    * <a href="https://leetcode.com/problems/search-in-a-binary-search-tree/description/" target="_blank">Search in a Binary Search Tree (leetcode)</a>


    * <a href="https://www.geeksforgeeks.org/problems/minimum-element-in-bst/1" target="_blank">Minimum element in BST (gfg)</a>




💯 🔥 🚀
