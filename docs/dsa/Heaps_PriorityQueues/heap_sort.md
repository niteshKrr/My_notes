# Heap Sort


## Heap Sort – Data Structures

**Heap sort** is a comparison-based sorting technique based on **Binary Heap** data structure. It is similar to the **selection sort** where we first find the minimum element and place the minimum element at the beginning. Repeat the same process for the remaining elements.


## Heap Sort Algorithm


* Build a heap from the given input array.
* Repeat the following steps until the heap contains only one element:
    * Swap the root element of the heap (which is the largest element) with the last element of the heap.
    * Remove the last element of the heap (which is now in the correct position).
    * Heapify the remaining elements of the heap.
* The sorted array is obtained by reversing the order of the elements in the input array.


---

### Code

```cpp

#include <iostream>
using namespace std;

void heapify(int arr[], int N, int i){

    // Initialize largest as root
    int largest = i;

    // left = 2*i + 1
    int l = 2 * i + 1;

    // right = 2*i + 2
    int r = 2 * i + 2;

    // If left child is larger than root
    if (l < N && arr[l] > arr[largest])
        largest = l;

    // If right child is larger than largest
    if (r < N && arr[r] > arr[largest])
        largest = r;

    // If largest is not root
    if (largest != i){
        swap(arr[i], arr[largest]);

        // Recursively heapify the affected sub-tree
        heapify(arr, N, largest);
    }
}

void heapSort(int arr[], int N){

    // Build heap (rearrange array)
    for (int i = N / 2 - 1; i >= 0; i--){
        heapify(arr, N, i);
    }

    for (int i = N - 1; i > 0; i--){
        swap(arr[i],arr[0]);
        heapify(arr, i, 0);
    }
    
}

void printArray(int arr[], int N){
    for (int i = 0; i < N; ++i)
        cout << arr[i] << " ";
    cout << endl;
}

int main(){

    int arr[] = { 12, 11, 13, 5, 6, 7 };
    int N = 6;

    heapSort(arr, N);

    cout << "Sorted array is \n";
    printArray(arr, N);
}



```