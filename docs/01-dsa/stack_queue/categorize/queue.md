# Queue Data Structure


## What is Queue ?

A **Queue** is a linear data structure that follows the **FIFO(First-In-First-Out)** principle. It operates like a line where elements are added at one end (**rear**) and removed from the other end (**front**).


![loading...](../../../images/dsa/stack_queue/Queue-Data-Structures.png)


---


## Operations on Queue :

* **Enqueue (Insert)**: Adds an element to the rear of the queue.
* **Dequeue (Delete)**: Removes and returns the element from the front of the queue.
* **Peek**: Returns the element at the front of the queue without removing it.
* **Empty**: Checks if the queue is empty.
* **Full**: Checks if the queue is full.


## Applications of Queue :

* **Task scheduling** in operating systems.
* **Data transfer** in network communication.


## Queue in C++ STL

```cpp

queue<data_type> name;


```

* **push(element)** – It pushes the value at the end of the queue – Time Complexity : O(1)
* **pop()** – It deletes the first element from the queue – Time Complexity : O(1)
* **size()** – It tells us the size of the queue – Time Complexity : O(1) 
* **front()** – It returns the first element of the queue – Time Complexity : O(1) 
* **back()** – It returns the last element of the queue – Time Complexity : O(1) 
* **empty()** – It tells us whether the queue is empty or not – Time Complexity : O(1)  



## Questions

💡 First try with yourself, if you are unable to do the question then see the solution.


??? tip "Implement Queue using Arrays"

    * <a href="https://www.geeksforgeeks.org/problems/implement-queue-using-array/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=implement-queue-using-array" target="_blank">Implement Queue using Arrays (gfg)</a>


    ---


    ```cpp

    #include <bits/stdc++.h>
    using namespace std;

    struct Queue {
        int front, rear, capacity;
        int* queue;
        Queue(int c){
            front = rear = 0;
            capacity = c;
            queue = new int[c];
        }

        ~Queue() { delete[] queue; }

        // function to insert an element
        void queueEnqueue(int data){
            // check queue is full or not
            if (capacity == rear) {
                printf("\nQueue is full\n");
                return;
            }

            // insert element at the rear
            else {
                queue[rear] = data;
                rear++;
            }
            return;
        }

        // function to delete an element
        void queueDequeue(){
            // if queue is empty
            if (front == rear) {
                printf("\nQueue is  empty\n");
                return;
            }

            // shift all the elements from index 2 till rear
            // to the left by one
            else {
                for (int i = 0; i < rear - 1; i++) {
                    queue[i] = queue[i + 1];
                }

                // decrement rear
                rear--;
            }
            return;
        }

        // print front of queue
        void queueFront(){
            if (front == rear) {
                printf("\nQueue is Empty\n");
                return;
            }
            printf("\nFront Element is: %d", queue[front]);
            return;
        }
    };

    int main(void){

        Queue q(4);

        // inserting elements in the queue
        q.queueEnqueue(20);
        q.queueEnqueue(30);
        q.queueEnqueue(40);
        q.queueEnqueue(50);

        // insert element in the queue
        q.queueEnqueue(60);

        q.queueDequeue();
        q.queueDequeue();


        // print front of the queue
        q.queueFront();

        return 0;
    }


    ```

??? tip "Implement Queue using Stacks"

    * <a href="https://leetcode.com/problems/implement-queue-using-stacks/description/" target="_blank">Implement Queue using Stacks (leetcode)</a>


    ---

    **Approach :**

    * For "push" function create two stacks (input and output), at every insertion transfer all elements from the stack "input" to "output" first then insert that element to the stack "input" and then transfer all elements from the stack "output" to "input".

    * And now perform all the operation on the stack "input" for desired output.

    **See the below code implementation.**

    ---



    ```cpp

    #include <bits/stdc++.h>
    using namespace std;

    struct Queue {

        stack < int > input, output;
        
        // Push elements in queue
        void Push(int data) {
            // Pop out all elements from the stack input
            while (!input.empty()) {
            output.push(input.top());
            input.pop();
            }
            // Insert the desired element in the stack input
            cout << "The element pushed is " << data << endl;
            input.push(data);
            // Pop out elements from the stack output and push them into the stack input
            while (!output.empty()) {
            input.push(output.top());
            output.pop();
            }
        }
        // Pop the element from the Queue
        int Pop() {
            if (input.empty()) {
            cout << "Stack is empty";
            exit(0);
            }
            int val = input.top();
            input.pop();
            return val;
        }
        // Return the Topmost element from the Queue
        int Top() {
            if (input.empty()) {
            cout << "Stack is empty";
            exit(0);
            }
            return input.top();
        }
        // Return the size of the Queue
        int size() {
            return input.size();
        }
    };
    int main() {

        Queue q;

        q.Push(3);
        q.Push(4);
        cout << "The element poped is " << q.Pop() << endl;
        q.Push(5);
        cout << "The top of the queue is " << q.Top() << endl;
        cout << "The size of the queue is " << q.size() << endl;
    }


    ```





💯 🔥 🚀


