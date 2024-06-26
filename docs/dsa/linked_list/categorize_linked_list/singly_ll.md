## Singly Linked List

It is the **simplest** type of linked list in which **every node** contains some data and a **pointer** to the **next node** of the same data type.


![loading...](../../../images/dsa/linked_list/singly-linkedlist.png)


---


### Implementation

??? abstract "See the code"

    ```cpp

    #include <bits/stdc++.h> 
    using namespace std; 

    // Structure of Node
    class Node{ 
      public: 
        int data;
        Node* next;

        Node(int data){
            this ->data = data;
            this ->next = NULL;
        }
    }; 

    Node* constructLL(vector<int>& arr) {

        if(arr.size() == 0){
            return NULL;
        }
            
        Node *Head = new Node(arr[0]);
        Node *temp = Head;
            
        for(int i = 1 ; i < arr.size() ; i++){
            Node* new_node = new Node(arr[i]);
            temp ->next = new_node;
            temp = temp ->next;
        }
            
        return Head;
    }
    
    void printList(Node* head){ 

        Node* temp = head;
        while (temp != NULL) { 

            cout << temp->data << " "; 
            temp = temp->next;
        } 
    }

    int main(){ 
         
        vector<int> arr = {1,2,3,4,5};

        Node *head = constructLL(arr);
        printList(head);
        cout<<endl;

        return 0; 
    }


    ```

---


## Questions

💡 First try with yourself, if you are unable to solve the question then see the solution.


??? tip "Linked List Insertion"

    * <a href="https://www.geeksforgeeks.org/problems/linked-list-insertion-1587115620/0?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=linked-list-insertion" target="_blank">Linked List Insertion (gfg)</a>


    ---


    ```cpp

    class Solution{
    public:
        //Function to insert a node at the beginning of the linked list.
        Node *insertAtBegining(Node *head, int x) {

            Node* new_node = new Node(x);
            new_node ->next = head;
            return new_node;
        }
        
        
        //Function to insert a node at the end of the linked list.
        Node *insertAtEnd(Node *head, int x)  {
        
            Node* new_node = new Node(x);
            if(head == NULL){
                return new_node;
            }
            Node* temp = head;
            Node* last = NULL;
            while(temp != NULL){
                last = temp;
                temp = temp ->next;
            }
            last ->next = new_node;
            
            return head;
        }
    };


    ```


??? tip "Deleting a node in LinkedList"

    * <a href="https://leetcode.com/problems/delete-node-in-a-linked-list/description/" target="_blank">Deleting a node in LinkedList (leetcode)</a>


    ---


    ```cpp

    class Solution {
      public:
        void deleteNode(ListNode* node) {
            
            ListNode* ahead_node = node ->next;
            node ->val = ahead_node ->val;
            node ->next = ahead_node ->next;

        }
    };


    ```

??? tip "Find the length of the linkedlist"

    * <a href="https://www.geeksforgeeks.org/problems/count-nodes-of-linked-list/0?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=count-nodes-of-linked-list" target="_blank">Find the length of the linkedlist (gfg)</a>


    ---


    ```cpp

    class Solution{
      public:
        int getCount(struct Node* head){
        
            int count = 0;
            Node* temp = head;
            while(temp != NULL){
                count++;
                temp = temp ->next;
            }
            
            return count;
        }
    };

    ```


??? tip "Search an element in the linkedlist"

    * <a href="https://www.geeksforgeeks.org/problems/search-in-linked-list-1664434326/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=search-in-linked-list-1664434326" target="_blank">Search an element in the linkedlist (gfg)</a>


    ---


    ```cpp

    class Solution {
      public:
        bool searchKey(int n, struct Node* head, int key) {
            
            Node* temp = head;
            while(temp != NULL){
                if(temp ->data == key){
                    return true;
                }
                temp = temp ->next;
            }
            return false;
        }
    };

    ```

??? tip "Deletion a node of given index"


    ```cpp

    Node* delete_node(Node* head , int index){

        if(head == NULL){
            return NULL;
        }
        if(head != NULL){
            if(index == 1){
                head = head ->next;
                return head;
            }
        }

        Node* pre = NULL;
        Node* temp = head;
        int count = 0;
        while(temp != NULL){
            count++;
            if(count == index){
                pre ->next = temp ->next;
                free(pre ->next);
            }
            pre = temp;
            temp = temp ->next;
        }
        return head;
    }
    

    ```


??? tip "Insertion a node of given index"


    ```cpp

    Node* insert_node(Node* head , int num , int idx){

        if(head == NULL){
            return NULL;
        }
        if(head != NULL){
            if(idx == 1){
                Node* temp = new Node(num);
                temp ->next = head;
                return temp;
            }
        }

        Node* pre = NULL;
        Node* temp = head;
        int count = 0;
        while(temp != NULL){
            count++;
            if(count == idx){
                Node* new_ele = new Node(num);
                pre ->next = new_ele;
                new_ele ->next = temp;
            }
            pre = temp;
            temp = temp ->next;
        } 
        return head;
    }


    ```


??? tip "Reverse a Linked List"

    * <a href="https://leetcode.com/problems/reverse-linked-list/description/" target="_blank">Reverse a Linked List (leetcode)</a>


    ---


    ```cpp

    class Solution {
      public:
        ListNode* reverseList(ListNode* head) {
            
            ListNode* curr = head;
            ListNode* pre = NULL;

            while(curr != NULL){
                ListNode* next = curr ->next;
                curr ->next = pre;
                pre = curr;
                curr = next;
            }

            return pre;
        }
    };


    ```

---

🥇 🥇 🥇


### Other Important Questions List

??? tip "Important Questions List"

    * <a href="https://leetcode.com/problems/middle-of-the-linked-list/description/" target="_blank">Middle of the Linked List (leetcode)</a>

    * <a href="https://leetcode.com/problems/linked-list-cycle/description/" target="_blank">Linked List cycle (leetcode)</a>

    * <a href="https://leetcode.com/problems/linked-list-cycle-ii/description/" target="_blank">Linked List cycle II (leetcode)</a>

    * <a href="https://www.geeksforgeeks.org/problems/find-length-of-loop/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=find-length-of-loop" target="_blank">Find length of Loop (gfg)</a>


    * <a href="https://leetcode.com/problems/palindrome-linked-list/description/" target="_blank">Check if LL is palindrome or not (leetcode)</a>


    * <a href="https://leetcode.com/problems/odd-even-linked-list/description/" target="_blank">Segrregate odd and even nodes in LL (leetcode)</a>
    

    * <a href="https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/" target="_blank">Remove Nth node from the back of the LL (leetcode)</a>


    * <a href="https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/" target="_blank">Delete the middle node of LL (leetcode)</a>


    * <a href="https://leetcode.com/problems/sort-list/description/" target="_blank">Sort LL (leetcode)</a>


    * <a href="https://www.geeksforgeeks.org/problems/given-a-linked-list-of-0s-1s-and-2s-sort-it/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=given-a-linked-list-of-0s-1s-and-2s-sort-it" target="_blank">Given a linked list of 0s, 1s and 2s, sort it (gfg)</a>


    * <a href="https://leetcode.com/problems/intersection-of-two-linked-lists/description/" target="_blank">Find the intersection point of LL (leetcode)</a>


    * <a href="https://www.geeksforgeeks.org/problems/add-1-to-a-number-represented-as-linked-list/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=add-1-to-a-number-represented-as-linked-list" target="_blank">Add 1 to a number represented as linked list (gfg)</a>


    * <a href="https://leetcode.com/problems/add-two-numbers/description/" target="_blank">Add two numbers in LL (leetcode)</a>



💯 🔥 🚀
