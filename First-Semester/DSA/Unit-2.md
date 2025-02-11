# Unit-2

## Array

```cpp
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

```cpp
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

```cpp
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

```cpp
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

```cpp
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

```cpp
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

```cpp
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

```cpp
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

---

## **C++ Streams and Console Stream Classes**

C++ **streams** provide a way to handle **input and output** operations using an abstraction called **streams**. Streams allow reading/writing from various devices like **keyboard, console, files, or memory buffers**.

### **1. What is a Stream?**

A **stream** in C++ is a sequence of bytes flowing between the program and an **I/O device** (console, file, network, etc.).  
📌 **Two types of streams:**  
✅ **Input Stream (istream)** → Reads data from an input source (e.g., keyboard, file).  
✅ **Output Stream (ostream)** → Writes data to an output source (e.g., console, file).

### **2. Console Stream Classes in C++**

C++ provides **iostream** library for console I/O.

| Stream Class   | Description                            |
| -------------- | -------------------------------------- |
| `istream`      | Base class for input stream            |
| `ostream`      | Base class for output stream           |
| `iostream`     | Combination of `istream` and `ostream` |
| `ifstream`     | Reads from files (input file stream)   |
| `ofstream`     | Writes to files (output file stream)   |
| `stringstream` | Reads/writes to a string buffer        |

### **3. Standard Console Streams**

C++ provides **three predefined console streams**:

| Stream | Class     | Purpose                            |
| ------ | --------- | ---------------------------------- |
| `cin`  | `istream` | Standard input stream (keyboard)   |
| `cout` | `ostream` | Standard output stream (console)   |
| `cerr` | `ostream` | Standard error stream (unbuffered) |
| `clog` | `ostream` | Standard error stream (buffered)   |

### **4. Basic Console I/O using Streams**

#### **Example: Basic `cin` and `cout`**

```cpp
#include <iostream>
using namespace std;

int main() {
    string name;
    int age;

    cout << "Enter your name: ";
    cin >> name; // Takes single word input

    cout << "Enter your age: ";
    cin >> age;

    cout << "Hello, " << name << "! You are " << age << " years old.\n";

    return 0;
}
```

📌 **Note:** `cin >>` reads a single word. To read a full sentence, use `getline(cin, name)`.

### **5. Using `cin.getline()` for Full-Line Input**

```cpp
#include <iostream>
using namespace std;

int main() {
    string name;

    cout << "Enter your full name: ";
    cin.ignore(); // Ignore newline if required
    getline(cin, name);

    cout << "Hello, " << name << "!\n";

    return 0;
}
```

✅ `getline(cin, name)` reads a **full line** including spaces.

### **6. Using `cerr` and `clog` for Error Handling**

- **`cerr`** → Prints error messages (unbuffered, appears instantly).
- **`clog`** → Used for logging messages (buffered, efficient for large output).

```cpp
#include <iostream>
using namespace std;

int main() {
    cerr << "Error: Invalid input!\n";  // Unbuffered error output
    clog << "Log: Execution started...\n";  // Buffered logging message

    return 0;
}
```

### **7. Stream Manipulators (`iomanip`)**

C++ provides the `<iomanip>` library for **formatting output**.

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    double pi = 3.14159265;

    cout << "Default: " << pi << endl;
    cout << "Fixed: " << fixed << pi << endl;
    cout << "Scientific: " << scientific << pi << endl;
    cout << "Precision 3: " << fixed << setprecision(3) << pi << endl;

    return 0;
}
```

📌 **Common manipulators**:
| Manipulator | Description |
|------------|-------------|
| `fixed` | Displays floating-point numbers in fixed notation |
| `scientific` | Displays numbers in scientific notation |
| `setw(n)` | Sets width for output |
| `setprecision(n)` | Controls decimal precision |
| `setfill(ch)` | Fills empty spaces with a character |

### **8. Chaining Console Streams**

You can chain multiple `cout` statements together.

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 20;
    cout << "The sum of " << a << " and " << b << " is " << (a + b) << endl;
    return 0;
}
```

### **9. Using `cin.fail()` for Input Validation**

```cpp
#include <iostream>
using namespace std;

int main() {
    int age;
    cout << "Enter your age: ";
    cin >> age;

    if (cin.fail()) {  // If input is invalid
        cerr << "Error: Invalid input! Please enter a number.\n";
        cin.clear();  // Clear error flag
        cin.ignore(1000, '\n'); // Ignore invalid input
    } else {
        cout << "Your age is: " << age << endl;
    }

    return 0;
}
```

📌 **`cin.fail()`** returns `true` if the input is not valid (e.g., entering a string instead of a number).

### **10. Buffered vs Unbuffered Streams**

| Stream | Type            | Buffered?       |
| ------ | --------------- | --------------- |
| `cout` | Standard output | Yes             |
| `cin`  | Standard input  | Yes             |
| `cerr` | Standard error  | No (unbuffered) |
| `clog` | Standard error  | Yes (buffered)  |

✅ **Unbuffered (`cerr`)** is printed immediately.  
✅ **Buffered (`cout`, `clog`)** waits until the buffer is flushed (e.g., with `endl`).

### **Conclusion**

🔹 **Streams** simplify input/output handling in C++.  
🔹 **`cin`, `cout`, `cerr`, `clog`** handle **console I/O efficiently**.  
🔹 **Stream manipulators** help in **formatting output**.  
🔹 **`cin.fail()`** prevents **invalid input issues**.

---

## **Formatted & Unformatted Console I/O Operations in C++**

C++ provides **two types of console I/O operations**:

1. **Formatted I/O** → Uses formatting tools like `setw()`, `setprecision()`, `endl`, etc.
2. **Unformatted I/O** → Reads/writes raw data using functions like `put()`, `get()`, `write()`, etc.

### **1. Formatted Console I/O**

**Formatted I/O operations** allow customization of input/output using **manipulators** from the `<iomanip>` library.

#### **Common Formatting Manipulators**

| Manipulator       | Description                                          |
| ----------------- | ---------------------------------------------------- |
| `setw(n)`         | Sets the width of the output field                   |
| `setprecision(n)` | Controls decimal places                              |
| `fixed`           | Prints floating-point numbers in fixed notation      |
| `scientific`      | Prints floating-point numbers in scientific notation |
| `setfill(ch)`     | Fills empty spaces with a character                  |
| `left`, `right`   | Aligns text to left or right                         |
| `boolalpha`       | Prints `true/false` instead of `1/0`                 |

#### **Example: Formatted Output using `<iomanip>`**

```cpp
#include <iostream>
#include <iomanip>  // Required for formatting
using namespace std;

int main() {
    double num = 123.456789;

    cout << "Default: " << num << endl;
    cout << "Fixed: " << fixed << num << endl;
    cout << "Scientific: " << scientific << num << endl;
    cout << "Precision 3: " << fixed << setprecision(3) << num << endl;

    cout << "\nRight-aligned: " << setw(10) << num << endl;
    cout << "Left-aligned: " << left << setw(10) << num << endl;
    cout << "Filled with *: " << setfill('*') << setw(10) << num << endl;

    return 0;
}
```

#### **Output**

```
Default: 123.457
Fixed: 123.456789
Scientific: 1.234568e+02
Precision 3: 123.457

Right-aligned:     123.457
Left-aligned: 123.457
Filled with *: ***123.457
```

📌 **Key Takeaways:**

- `setprecision(n)` **controls decimal places**.
- `setw(n)` **sets width** for alignment.
- `setfill('*')` **fills empty spaces with a character**.
- `fixed` **prints floating points normally**, while `scientific` **uses exponent notation**.

### **2. Unformatted Console I/O**

**Unformatted I/O operations** directly read/write characters without formatting.

#### **Common Unformatted Functions**

| Function        | Description                                         |
| --------------- | --------------------------------------------------- |
| `get()`         | Reads a **single character** (including whitespace) |
| `getline()`     | Reads a **whole line** including spaces             |
| `put(ch)`       | Writes a **single character** to the console        |
| `write(str, n)` | Writes a string of **n characters**                 |

#### **Example: `get()`, `put()`**

```cpp
#include <iostream>
using namespace std;

int main() {
    char ch;

    cout << "Enter a character: ";
    ch = cin.get();  // Reads one character including whitespace

    cout << "You entered: ";
    cout.put(ch);    // Outputs a single character

    return 0;
}
```

#### **Output**

```
Enter a character: A
You entered: A
```

📌 **Key Takeaways:**

- `cin.get()` reads **one character at a time**, including spaces.
- `cout.put()` outputs a **single character**.

#### **Example: `getline()` for Full-Line Input**

```cpp
#include <iostream>
using namespace std;

int main() {
    string name;

    cout << "Enter your full name: ";
    getline(cin, name);  // Reads entire line including spaces

    cout << "Hello, " << name << "!\n";

    return 0;
}
```

#### **Output**

```
Enter your full name: John Doe
Hello, John Doe!
```

📌 **Key Takeaways:**

- `getline(cin, str)` **reads a full line** including spaces.

#### **Example: `write()` for Writing Fixed-Length Strings**

```cpp
#include <iostream>
using namespace std;

int main() {
    char text[] = "HelloWorld";

    cout.write(text, 5);  // Writes only first 5 characters
    cout << endl;

    return 0;
}
```

#### **Output**

```
Hello
```

📌 **Key Takeaways:**

- `cout.write(str, n)` **outputs only the first `n` characters**.

### **3. Difference Between Formatted & Unformatted I/O**

| Feature               | Formatted I/O                                           | Unformatted I/O                        |
| --------------------- | ------------------------------------------------------- | -------------------------------------- |
| **Functions**         | `cout`, `cin`, `setw()`, `setprecision()`               | `get()`, `put()`, `write()`            |
| **Spaces & Newlines** | Ignores spaces/newlines                                 | Reads everything, including spaces     |
| **Usage**             | Used for formatted output (tables, decimals, alignment) | Used for raw data (character handling) |

### **Conclusion**

- **Formatted I/O** (`setw()`, `setprecision()`, `setfill()`) is useful for **better presentation** of data.
- **Unformatted I/O** (`get()`, `put()`, `write()`) is **faster and used for raw character input/output**.
- **Use `getline()` instead of `cin`** when reading full-line input with spaces.

---

## **File Streams, File Pointers, and File I/O in C++**

C++ provides powerful file handling capabilities using the **fstream** library. File I/O operations allow programs to read from and write to files.

### **1. File Streams in C++**

C++ uses **stream classes** from the `<fstream>` library for file handling:

| Stream Class | Description                           |
| ------------ | ------------------------------------- |
| `ifstream`   | Input file stream (reads from a file) |
| `ofstream`   | Output file stream (writes to a file) |
| `fstream`    | Both input and output file stream     |

📌 **Header file required:**

```cpp
#include <fstream>
```

### **2. Opening and Closing Files**

To work with files, we must:

1. **Open** the file.
2. **Perform read/write operations.**
3. **Close** the file to free resources.

#### **Example: Writing to a File**

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream file("example.txt"); // Open file for writing

    if (!file) {
        cerr << "Error opening file!" << endl;
        return 1;
    }

    file << "Hello, File I/O in C++!" << endl; // Write to file
    file.close();  // Close file

    cout << "Data written to file successfully!" << endl;
    return 0;
}
```

📌 **Key Takeaways:**

- `ofstream file("example.txt");` opens the file in **write mode**.
- `file << "Text";` writes data to the file.
- `file.close();` closes the file.

#### **Example: Reading from a File**

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream file("example.txt"); // Open file for reading
    string line;

    if (!file) {
        cerr << "Error opening file!" << endl;
        return 1;
    }

    while (getline(file, line)) { // Read line by line
        cout << line << endl;
    }

    file.close(); // Close file
    return 0;
}
```

📌 **Key Takeaways:**

- `ifstream file("example.txt");` opens the file in **read mode**.
- `getline(file, line);` reads one line at a time.

### **3. File Opening Modes**

File modes determine how a file is opened and modified.

| Mode          | Description                                |
| ------------- | ------------------------------------------ |
| `ios::in`     | Open for reading                           |
| `ios::out`    | Open for writing (erases previous content) |
| `ios::app`    | Append data at the end                     |
| `ios::ate`    | Open and move to the end                   |
| `ios::trunc`  | Truncate file (delete previous content)    |
| `ios::binary` | Open in binary mode                        |

#### **Example: Opening a File in Append Mode**

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream file("example.txt", ios::app); // Open in append mode

    if (!file) {
        cerr << "Error opening file!" << endl;
        return 1;
    }

    file << "Appending new data!" << endl; // Appends data
    file.close();

    cout << "Data appended successfully!" << endl;
    return 0;
}
```

📌 **Key Takeaways:**

- `ios::app` **keeps previous data** and **adds new content**.

### **4. File Pointers and Manipulation**

C++ provides **file pointers** to control the **read/write position** inside a file.

#### **Types of File Pointers**

| Pointer              | Function                         |
| -------------------- | -------------------------------- |
| `get pointer (gptr)` | Used for **reading** from a file |
| `put pointer (pptr)` | Used for **writing** to a file   |

#### **Functions to Manipulate File Pointers**

| Function          | Description                                   |
| ----------------- | --------------------------------------------- |
| `seekg(pos, dir)` | Moves **get pointer** to position `pos`       |
| `seekp(pos, dir)` | Moves **put pointer** to position `pos`       |
| `tellg()`         | Returns **current position** of `get pointer` |
| `tellp()`         | Returns **current position** of `put pointer` |

📌 **`dir` values:**

- `ios::beg` → Beginning of the file.
- `ios::cur` → Current position.
- `ios::end` → End of the file.

#### **Example: Using File Pointers**

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    fstream file("example.txt", ios::in | ios::out); // Open in read/write mode

    if (!file) {
        cerr << "Error opening file!" << endl;
        return 1;
    }

    file.seekg(0, ios::end); // Move to end
    int size = file.tellg(); // Get current position (file size)
    cout << "File size: " << size << " bytes" << endl;

    file.seekg(0, ios::beg); // Move back to the beginning
    string line;
    getline(file, line);
    cout << "First line: " << line << endl;

    file.close();
    return 0;
}
```

📌 **Key Takeaways:**

- `tellg()` **gets file size** (when at the end).
- `seekg(0, ios::beg)` **moves pointer to start**.

### **5. Reading and Writing Objects to a File**

#### **Example: Writing and Reading a Class Object**

```cpp
#include <iostream>
#include <fstream>
using namespace std;

class Student {
public:
    char name[30];
    int age;

    void getData() {
        cout << "Enter Name: ";
        cin >> name;
        cout << "Enter Age: ";
        cin >> age;
    }

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Student s1;
    s1.getData();

    // Writing object to file
    ofstream file("student.dat", ios::binary);
    file.write(reinterpret_cast<char*>(&s1), sizeof(s1));
    file.close();

    // Reading object from file
    Student s2;
    ifstream inFile("student.dat", ios::binary);
    inFile.read(reinterpret_cast<char*>(&s2), sizeof(s2));
    inFile.close();

    cout << "Data read from file:\n";
    s2.display();

    return 0;
}
```

📌 **Key Takeaways:**

- `write(reinterpret_cast<char*>(&obj), sizeof(obj))` **writes binary data**.
- `read(reinterpret_cast<char*>(&obj), sizeof(obj))` **reads binary data**.

### **Conclusion**

✅ **`ifstream`, `ofstream`, `fstream`** provide powerful file I/O operations.  
✅ **Modes (`ios::app`, `ios::binary`)** control file behavior.  
✅ **File pointers (`seekg`, `seekp`)** allow direct navigation.  
✅ **Binary file handling (`write`, `read`)** is used for **storing objects** efficiently.

---

## **Error Handling in C++**

Errors can be handled using:

1. **Exception Handling (`try`, `catch`, `throw`)**
2. **Error Codes (`if` conditions)**
3. **`errno` and `perror()` for system errors**

### **1.1 Exception Handling (`try`, `catch`, `throw`)**

C++ provides the **exception handling mechanism** using:

- `throw` → Used to **raise an exception**.
- `try` → Wraps the code where an exception might occur.
- `catch` → Handles the exception.

#### **Example: Handling Division by Zero**

```cpp
#include <iostream>
using namespace std;

double divide(int a, int b) {
    if (b == 0)
        throw "Division by zero error!";  // Throwing an exception
    return (double)a / b;
}

int main() {
    try {
        cout << "Result: " << divide(10, 0) << endl;
    }
    catch (const char* msg) {
        cerr << "Exception: " << msg << endl;
    }
    return 0;
}
```

#### **Output**

```
Exception: Division by zero error!
```

📌 **Key Takeaways:**

- `throw` **raises an exception**.
- `catch` **handles the exception**.
- Exceptions can be of **any type (int, string, objects, etc.)**.

### **1.2 Multiple `catch` Blocks**

```cpp
#include <iostream>
using namespace std;

void test(int num) {
    if (num == 0)
        throw 0;  // Throwing an integer
    else if (num == 1)
        throw "String Exception";
    else
        throw 1.5; // Throwing a double
}

int main() {
    try {
        test(1);
    }
    catch (int e) {
        cout << "Caught an integer: " << e << endl;
    }
    catch (const char* e) {
        cout << "Caught a string: " << e << endl;
    }
    catch (...) {  // Catch-all handler
        cout << "Caught an unknown exception!" << endl;
    }
    return 0;
}
```

#### **Output**

```
Caught a string: String Exception
```

📌 **Key Takeaways:**

- Multiple `catch` blocks **handle different exception types**.
- The `catch(...)` block **catches all remaining exceptions**.

### **1.3 Standard Exception Classes**

C++ provides predefined **exception classes** in `<stdexcept>`:

| Exception Class      | Description                              |
| -------------------- | ---------------------------------------- |
| `std::exception`     | Base class for all exceptions            |
| `std::runtime_error` | Runtime errors (e.g., division by zero)  |
| `std::logic_error`   | Logical errors (e.g., invalid arguments) |
| `std::out_of_range`  | Accessing out-of-bound array elements    |

#### **Example: Using `std::runtime_error`**

```cpp
#include <iostream>
#include <stdexcept>  // Required for standard exceptions
using namespace std;

int main() {
    try {
        throw runtime_error("Custom runtime error!");
    }
    catch (const exception& e) {
        cout << "Caught Exception: " << e.what() << endl;
    }
    return 0;
}
```

#### **Output**

```
Caught Exception: Custom runtime error!
```

📌 **`e.what()`** returns the error message.

---

## **Dynamic Memory Allocation in C++**

Dynamic memory allocation allows allocating memory at runtime using:

- `new` → Allocates memory dynamically.
- `delete` → Frees allocated memory.

### **2.1 Allocating and Deallocating Memory (`new` and `delete`)**

```cpp
#include <iostream>
using namespace std;

int main() {
    int* ptr = new int;  // Dynamically allocate an integer
    *ptr = 100;
    cout << "Value: " << *ptr << endl;

    delete ptr; // Free allocated memory
    return 0;
}
```

📌 **Key Takeaways:**

- `new int` → Allocates memory for an integer.
- `delete ptr` → Frees the allocated memory.

### **2.2 Allocating Arrays Dynamically**

```cpp
#include <iostream>
using namespace std;

int main() {
    int* arr = new int[5]; // Allocate array of 5 integers

    for (int i = 0; i < 5; i++)
        arr[i] = i * 10;  // Assign values

    cout << "Array Elements: ";
    for (int i = 0; i < 5; i++)
        cout << arr[i] << " ";

    delete[] arr;  // Free memory allocated for array
    return 0;
}
```

#### **Output**

```
Array Elements: 0 10 20 30 40
```

📌 **Use `delete[] ptr;`** to deallocate arrays.

### **2.3 Handling Memory Allocation Failure (`nothrow`)**

If memory allocation fails, `new` throws a `bad_alloc` exception. To **handle failure**:

```cpp
#include <iostream>
using namespace std;

int main() {
    int* ptr = new(nothrow) int[1000000000000];  // Large allocation

    if (!ptr)
        cout << "Memory allocation failed!" << endl;
    else {
        cout << "Memory allocation successful!" << endl;
        delete[] ptr; // Free memory
    }

    return 0;
}
```

## 📌 **`new(nothrow)`** returns **NULL instead of throwing an exception**.

---

## **Smart Pointers (Automatic Memory Management)**

C++11 introduced **smart pointers** in `<memory>` to **avoid memory leaks**.

### **3.1 `unique_ptr` (Auto-deletes Memory)**

```cpp
#include <iostream>
#include <memory> // Required for smart pointers
using namespace std;

int main() {
    unique_ptr<int> ptr(new int(50));
    cout << "Value: " << *ptr << endl;  // No need to delete manually
    return 0;
}
```

📌 **`unique_ptr` deletes memory automatically when it goes out of scope.**

### **3.2 `shared_ptr` (Shared Ownership)**

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    shared_ptr<int> ptr1 = make_shared<int>(100);
    shared_ptr<int> ptr2 = ptr1; // Both share ownership

    cout << "Value: " << *ptr1 << ", " << *ptr2 << endl;
    return 0;
}
```

📌 **`shared_ptr` keeps a reference count** and deletes memory when **no owners remain**.

### **3.3 `weak_ptr` (Prevents Cyclic References)**

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    shared_ptr<int> sp = make_shared<int>(42);
    weak_ptr<int> wp = sp; // Does not increase reference count

    if (auto p = wp.lock())  // Check if object exists
        cout << "Value: " << *p << endl;
    else
        cout << "Memory already freed!" << endl;

    return 0;
}
```

📌 **`weak_ptr` prevents memory leaks in cyclic references.**

### **Conclusion**

✅ **Exception Handling (`try-catch`)** prevents program crashes.  
✅ **Dynamic Memory (`new`, `delete`)** manages heap memory efficiently.  
✅ **Smart Pointers (`unique_ptr`, `shared_ptr`)** **prevent memory leaks** automatically.  
✅ **`nothrow` & `bad_alloc`** handle memory allocation failures.

---

## **`Gagan Saini`**
