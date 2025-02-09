# Unit-2

## Array

```
int main()
{
    int n;
    cin >> n;

    int arr[n];

    // Input Array
    for (int i = 0; i < n; i++)
    {
        cin >> arr[i];
    }

    // Print Array
    for (int i = 0; i < n; i++)
    {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

## 2D Array (Matrix)

```
int main()
{
    int n, m;
    cin >> n >> m;

    int arr[n][m];

    // Input Matrix
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < m; j++)
        {
            cin >> arr[i][j];
        }
    }

    // Print Array
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < m; j++)
        {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

---

## Linear & Binary Search

Here is the **C++ code** for **Linear Search** and **Binary Search**, along with explanations and example outputs.

### **1. Linear Search**

- **Time Complexity:** \(O(n)\) (worst case)
- **Works on:** Unsorted or sorted arrays
- **How it works:**
  - Iterate through the array sequentially.
  - If the target element is found, return its index.
  - If the loop ends without finding the element, return `-1`.

#### **C++ Code for Linear Search**

```cpp
#include <iostream>
using namespace std;

int linearSearch(int arr[], int size, int key) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == key)
            return i; // Return index if found
    }
    return -1; // Not found
}

int main() {
    int arr[] = {10, 25, 30, 45, 50, 60};
    int size = sizeof(arr) / sizeof(arr[0]);
    int key = 45;

    int index = linearSearch(arr, size, key);

    if (index != -1)
        cout << "Element found at index: " << index << endl;
    else
        cout << "Element not found!" << endl;

    return 0;
}
```

#### **2. Binary Search**

- **Time Complexity:** \(O(\log n)\)
- **Works on:** **Sorted arrays only**
- **How it works:**
  - Find the middle element.
  - If the middle element is the target, return its index.
  - If the target is **smaller**, search the left half.
  - If the target is **greater**, search the right half.
  - Repeat until the element is found or the search space becomes empty.

#### **C++ Code for Binary Search (Iterative)**

```cpp
#include <iostream>
using namespace std;

// Function for Binary Search (Iterative)
int binarySearch(int arr[], int size, int key) {
    int left = 0, right = size - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == key)
            return mid; // Found

        if (arr[mid] < key)
            left = mid + 1; // Search right half
        else
            right = mid - 1; // Search left half
    }
    return -1; // Not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50, 60};
    int size = sizeof(arr) / sizeof(arr[0]);
    int key = 40;

    int index = binarySearch(arr, size, key);

    if (index != -1)
        cout << "Element found at index: " << index << endl;
    else
        cout << "Element not found!" << endl;

    return 0;
}
```

### **3. Binary Search (Recursive)**

This is another way to implement binary search using recursion.

```cpp
#include <iostream>
using namespace std;

int binarySearchRecursive(int arr[], int left, int right, int key) {
    if (left > right) return -1; // Base case: Not found

    int mid = left + (right - left) / 2;

    if (arr[mid] == key) return mid; // Found
    if (arr[mid] < key)
        return binarySearchRecursive(arr, mid + 1, right, key); // Right half
    else
        return binarySearchRecursive(arr, left, mid - 1, key); // Left half
}

int main() {
    int arr[] = {5, 10, 15, 20, 25, 30, 35};
    // int size = sizeof(arr) / sizeof(arr[0]);
    int size = 7;
    int key = 15;

    int index = binarySearchRecursive(arr, 0, size - 1, key);

    if (index != -1)
        cout << "Element found at index: " << index << endl;
    else
        cout << "Element not found!" << endl;

    return 0;
}
```

### **Comparison: Linear Search vs. Binary Search**

| Feature              | Linear Search           | Binary Search                                    |
| -------------------- | ----------------------- | ------------------------------------------------ |
| **Time Complexity**  | \(O(n)\) (Worst Case)   | \(O(\log n)\)                                    |
| **Best for**         | Small or unsorted lists | Large sorted lists                               |
| **Implementation**   | Simple                  | Requires sorting first                           |
| **Space Complexity** | \(O(1)\)                | \(O(1)\) (Iterative) / \(O(\log n)\) (Recursive) |
| **Works on**         | Unsorted & sorted data  | Only sorted data                                 |

### **Conclusion**

- Use **Linear Search** for small or unsorted datasets.
- Use **Binary Search** for sorted data for fast searching.
- **Recursive Binary Search** is elegant but has additional function calls.

---

## Sorting

1. **Insertion Sort**

```
void insertionSort(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        for (int j = i + 1; j < n; j++)
        {
            if (arr[i] > arr[j])
                swap(arr[i], arr[j]);
        }
    }
}

```

2. **Bubble Sort**

```
void bubbleSort(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n - i - 1; j++)
        {
            if (arr[j] > arr[j + 1])
                swap(arr[j], arr[j + 1]);
        }
    }
}
```

3. **Selection Sort**

```
void selectionSort(int arr[], int n)
{
    int firstIndex = 0;
    int idx = 0;

    for (int i = 0; i < n; i++)
    {
        int mini = INT32_MAX;
        for (int j = firstIndex; j < n; j++)
        {
            if (arr[j] < mini)
            {
                mini = arr[j];
                idx = j;
            }
        }

        swap(arr[idx], arr[firstIndex]);
        firstIndex++;
    }
}
```

4.  **Merge Sort**

```
void merge(int arr[], int s, int mid, int e)
{
    int n1 = mid - s + 1;
    int n2 = e - mid;

    int first[n1];
    int second[n2];

    for (int i = 0; i < n1; i++)
    {
        first[i] = arr[s + i];
    }
    for (int j = 0; j < n2; j++)
    {
        second[j] = arr[mid + 1 + j];
    }

    int i = 0, j = 0, k = s;

    while (i < n1 && j < n2)
    {
        if (first[i] < second[j])
        {
            arr[k] = first[i];
            i++;
        }
        else
        {
            arr[k] = second[j];
            j++;
        }
        k++;
    }

    while (i < n1)
    {
        arr[k] = first[i];
        i++;
        k++;
    }

    while (j < n2)
    {
        arr[k] = second[j];
        j++;
        k++;
    }
}

void mergeSort(int arr[], int s, int e)
{
    if (s < e)
    {
        int mid = s + (e - s) / 2;
        mergeSort(arr, s, mid);
        mergeSort(arr, mid + 1, e);
        merge(arr, s, mid, e);
    }
}
```

5. **Quick Sort**

TC -> Best Case -> O(NlogN) & Average Case -> O(NlogN) & Worst Case -> O(N^2)
SC -> O(N)

```
int parition(int arr[], int s, int e)
{
    // Step 1: Find the Pivot Point.
    int pivot = arr[s];
    int count = 0;
    for (int i = s + 1; i <= e; i++)
    {
        if (arr[i] <= pivot)
            count++;
    }

    int pivotIndex = s + count;
    // Step 2: Place the pivot point at right place by counting smaller element from it.
    swap(arr[s], arr[pivotIndex]);

    // Step 3: Move all small element from pivot to left side to pivot & greater elements to right.
    int i = s, j = e;

    while (i < pivotIndex && j > pivotIndex)
    {
        while (arr[i] < pivot)
        {
            i++;
        }

        while (arr[j] > pivot)
        {
            j--;
        }

        if (i < pivotIndex && j > pivotIndex)
        {
            swap(arr[i], arr[j]);
            i++;
            j--;
        }
    }

    return pivotIndex;
}

void quickSort(int arr[], int s, int e)
{
    if (s >= e)
        return;

    int idx = parition(arr, s, e);
    quickSort(arr, s, idx - 1);
    quickSort(arr, idx + 1, e);
}
```

### Main Function

```
int main()
{
    int n;
    cin >> n;
    int arr[n];
    for (int i = 0; i < n; i++)
        cin >> arr[i];

    // Uncomment one at a time to use

    insertionSort(arr, n);
    // bubbleSort(arr, n);
    // selectionSort(arr, n);
    // mergeSort(arr, 0, n - 1);
    // quickSort(arr, 0, n - 1);

    cout << "Sorted Array: ";

    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";

    cout << endl;

    return 0;
}
```

6. **Radix Sort**

Radix Sort is a **non-comparative sorting algorithm** that sorts numbers digit by digit, from the least significant digit (LSD) to the most significant digit (MSD), using a stable sorting algorithm like **Counting Sort** as a subroutine.

### **Time Complexity**

- **Best Case:** \( O(nk) \)
- **Average Case:** \( O(nk) \)
- **Worst Case:** \( O(nk) \)
  - \( n \) = number of elements
  - \( k \) = number of digits in the largest number

### **Steps of Radix Sort**

1. Find the maximum number in the array to determine the number of digits.
2. Apply **Counting Sort** for each digit (unit place, tens place, hundreds place, etc.).
3. Continue until all digits are processed.

### **C++ Implementation of Radix Sort**

```cpp

#include <iostream>
using namespace std;

// Function to get the maximum number in the array
int getMax(int arr[], int n) {
    int maxVal = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > maxVal)
            maxVal = arr[i];
    return maxVal;
}

// Counting Sort (Stable) used for each digit position
void countingSort(int arr[], int n, int exp) {
    int output[n]; // Output array
    int count[10] = {0}; // Count array (digits 0-9)

    // Count occurrences of each digit
    for (int i = 0; i < n; i++)
        count[(arr[i] / exp) % 10]++;

    // Modify count[i] to store actual position in output[]
    for (int i = 1; i < 10; i++)
        count[i] += count[i - 1];

    // Build the output array
    for (int i = n - 1; i >= 0; i--) {
        output[count[(arr[i] / exp) % 10] - 1] = arr[i];
        count[(arr[i] / exp) % 10]--;
    }

    // Copy sorted values back to original array
    for (int i = 0; i < n; i++)
        arr[i] = output[i];
}

// Radix Sort Function
void radixSort(int arr[], int n) {
    int maxVal = getMax(arr, n); // Find the maximum number

    // Apply counting sort to each digit (LSD to MSD)
    for (int exp = 1; maxVal / exp > 0; exp *= 10)
        countingSort(arr, n, exp);
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {170, 45, 75, 90, 802, 24, 2, 66};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    radixSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

### **Key Points**

✅ **Stable Sorting Algorithm** – Maintains the order of duplicate values.  
✅ **Efficient for Large Numbers** – Works well for numbers with multiple digits.  
✅ **Better for Fixed-Length Numbers** – Especially useful when range is limited.  
❌ **Not In-Place** – Requires extra space for intermediate sorting.

7. **Shell Sort**

**Shell Sort** is an **improved version of Insertion Sort** that works by sorting elements at a gap, reducing the gap, and eventually performing a final **Insertion Sort** when the gap becomes 1.

### **Time Complexity**

- **Best Case:** \( O(n \log n) \)
- **Average Case:** \( O(n^{3/2}) \)
- **Worst Case:** \( O(n^2) \)

### **Working of Shell Sort**

1. **Choose a gap sequence** (e.g., `n/2`, `n/4`, ..., `1`).
2. **Perform gapped insertion sort** for each gap.
3. **Reduce the gap** and repeat until the array is sorted.

### **C++ Implementation of Shell Sort**

```cpp
#include <iostream>
using namespace std;

void shellSort(int arr[], int n) {
    // Start with a big gap, then reduce it
    for (int gap = n / 2; gap > 0; gap /= 2) {
        // Perform insertion sort for elements at the given gap
        for (int i = gap; i < n; i++) {
            int temp = arr[i];
            int j;

            // Shift earlier gap-sorted elements
            for (j = i; j >= gap && arr[j - gap] > temp; j -= gap) {
                arr[j] = arr[j - gap];
            }

            // Place temp (original arr[i]) in its correct location
            arr[j] = temp;
        }
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {12, 34, 54, 2, 3, 1, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    shellSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

### **Key Points**

✅ **Faster than Insertion Sort** – Reduces the number of swaps by sorting at a gap.  
✅ **Efficient for Medium-Sized Data Sets** – Performs well on moderately large arrays.  
✅ **Works Well for Partially Sorted Data** – Useful when data is nearly sorted.  
❌ **Not a Stable Sort** – Relative order of equal elements may change.
