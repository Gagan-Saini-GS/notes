# Unit-4

## Threaded Binary Tree

A **Threaded Binary Tree** is a special type of binary tree that makes use of unused NULL pointers in leaf nodes to store additional information, often enabling **faster in-order, pre-order, or post-order traversals** without using a stack or recursion.

### **Types of Threaded Binary Trees**

1. **Single Threaded** – Only **left or right** child pointers are used for threading.
2. **Double Threaded** – Both **left and right** child pointers are used for threading.

### **Advantages**

✅ **Faster Traversals** – No need for recursion or an explicit stack.  
✅ **Efficient Space Utilization** – Reduces memory overhead by using NULL pointers.  
✅ **Easier Successor/Predecessor Access** – Quickly find the next or previous node in traversal order.

### **Example of a Right Threaded Binary Tree**

```
       10
      /  \
     5    20
         /  \
        15   25
```

In a right-threaded binary tree, the **right NULL pointers** are replaced with **in-order successors**.

Here’s a **C++ implementation** of a **Threaded Binary Tree** with **in-order traversal**:

### **Implementation of Right-Threaded Binary Tree**

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node *left, *right;
    bool isThreaded; // True if right pointer is a thread (not a real child)

    Node(int val) {
        data = val;
        left = right = nullptr;
        isThreaded = false;
    }
};

class ThreadedBinaryTree {
private:
    Node* root;

    // Helper function to insert a node
    Node* insert(Node* root, int key) {
        if (!root)
            return new Node(key);

        if (key < root->data) {
            root->left = insert(root->left, key);
        } else {
            if (root->right == nullptr || root->isThreaded) {
                Node* newNode = new Node(key);
                newNode->right = root->right;
                newNode->isThreaded = true;
                root->right = newNode;
                root->isThreaded = false;
            } else {
                root->right = insert(root->right, key);
            }
        }
        return root;
    }

    // Leftmost node (smallest value in BST)
    Node* leftMost(Node* node) {
        while (node && node->left)
            node = node->left;
        return node;
    }

public:
    ThreadedBinaryTree() { root = nullptr; }

    void insert(int key) { root = insert(root, key); }

    // Inorder traversal using threading
    void inorder() {
        Node* current = leftMost(root);
        while (current) {
            cout << current->data << " ";
            if (current->isThreaded)
                current = current->right;
            else
                current = leftMost(current->right);
        }
    }
};

int main() {
    ThreadedBinaryTree tbt;
    tbt.insert(20);
    tbt.insert(10);
    tbt.insert(30);
    tbt.insert(5);
    tbt.insert(15);
    tbt.insert(25);
    tbt.insert(35);

    cout << "Inorder Traversal: ";
    tbt.inorder();
    cout << endl;

    return 0;
}
```

### **Explanation**

1. **Insertion (`insert` function)**
   - Nodes are inserted as in a normal **Binary Search Tree (BST)**.
   - If a node has no right child, it is **threaded** to its **in-order successor**.
2. **Traversal (`inorder` function)**
   - Finds the **leftmost node** (smallest value).
   - Iterates using **threaded pointers** instead of recursion.

### **Output**

```
Inorder Traversal: 5 10 15 20 25 30 35
```

This implementation efficiently traverses the tree **without recursion or a stack**, using **threaded pointers**.

---

## Tree Sort

Tree Sort is a **comparison-based sorting algorithm** that builds a **Binary Search Tree (BST)** from the input data and then performs an **in-order traversal** to retrieve the sorted elements.

### **Steps for Tree Sort**

1. **Insert** all elements into a **BST**.
2. **Perform an in-order traversal** to retrieve elements in sorted order.

### **C++ Implementation**

```cpp
#include <iostream>
using namespace std;

// Node structure for BST
class Node {
public:
    int data;
    Node *left, *right;

    Node(int value) {
        data = value;
        left = right = nullptr;
    }
};

// Function to insert a node into BST
Node* insert(Node* root, int value) {
    if (root == nullptr) {
        return new Node(value);
    }
    if (value < root->data)
        root->left = insert(root->left, value);
    else
        root->right = insert(root->right, value);

    return root;
}

// In-order traversal to retrieve sorted values
void inorder(Node* root) {
    if (root != nullptr) {
        inorder(root->left);
        cout << root->data << " ";
        inorder(root->right);
    }
}

// Function to perform Tree Sort
void treeSort(int arr[], int n) {
    Node* root = nullptr;

    // Insert elements into BST
    for (int i = 0; i < n; i++) {
        root = insert(root, arr[i]);
    }

    // Print sorted elements using in-order traversal
    cout << "Sorted Array: ";
    inorder(root);
    cout << endl;
}

// Driver Code
int main() {
    int arr[] = {5, 3, 7, 10, 1, 8};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original Array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    treeSort(arr, n);

    return 0;
}
```

### **Explanation**

1. **Insertion (`insert` function)**

   - Each element is inserted into a **BST**, maintaining the BST properties.

2. **Sorting (`inorder` function)**

   - In-order traversal of a BST prints elements in **sorted order**.

3. **Time Complexity**
   - **Best/Average Case:** **O(n log n)** (Balanced BST)
   - **Worst Case:** **O(n²)** (Skewed BST, like when inserting sorted data)

### **Output**

```
Original Array: 5 3 7 10 1 8
Sorted Array: 1 3 5 7 8 10
```

This implementation is **simple and efficient**, but for better performance, **self-balancing BSTs (like AVL or Red-Black Trees)** can be used to ensure **O(n log n)** complexity in all cases.

---

## **Trie Data Structure**

A **Trie (Prefix Tree)** is a tree-like data structure used for **efficient string searching, insertion, and auto-completion**.

### **Trie Operations**

✅ **Insert** – Add words to the trie.  
✅ **Search** – Check if a word exists.  
✅ **StartsWith (Prefix Search)** – Find words with a given prefix.

### **C++ Implementation of Trie**

```cpp
#include <iostream>
using namespace std;

#define ALPHABET_SIZE 26

// Trie Node
class TrieNode {
public:
    TrieNode* children[ALPHABET_SIZE]; // Array of child pointers
    bool isEndOfWord; // True if word ends at this node

    TrieNode() {
        isEndOfWord = false;
        for (int i = 0; i < ALPHABET_SIZE; i++)
            children[i] = nullptr;
    }
};

// Trie Class
class Trie {
private:
    TrieNode* root;

public:
    Trie() {
        root = new TrieNode();
    }

    // Insert a word into the Trie
    void insert(string word) {
        TrieNode* node = root;
        for (char c : word) {
            int index = c - 'a';
            if (!node->children[index])
                node->children[index] = new TrieNode();
            node = node->children[index];
        }
        node->isEndOfWord = true;
    }

    // Search for a word in the Trie
    bool search(string word) {
        TrieNode* node = root;
        for (char c : word) {
            int index = c - 'a';
            if (!node->children[index])
                return false;
            node = node->children[index];
        }
        return node->isEndOfWord;
    }

    // Check if a prefix exists in the Trie
    bool startsWith(string prefix) {
        TrieNode* node = root;
        for (char c : prefix) {
            int index = c - 'a';
            if (!node->children[index])
                return false;
            node = node->children[index];
        }
        return true;
    }
};

// Driver Code
int main() {
    Trie trie;
    trie.insert("apple");
    trie.insert("app");

    cout << "Search 'apple': " << (trie.search("apple") ? "Found" : "Not Found") << endl;
    cout << "Search 'app': " << (trie.search("app") ? "Found" : "Not Found") << endl;
    cout << "Prefix 'ap': " << (trie.startsWith("ap") ? "Exists" : "Does Not Exist") << endl;
    cout << "Search 'banana': " << (trie.search("banana") ? "Found" : "Not Found") << endl;

    return 0;
}
```

### **Explanation**

1. **Insertion (`insert` function)**

   - Characters of the word are added level by level.
   - `isEndOfWord` is marked at the last character.

2. **Search (`search` function)**

   - Checks if all characters exist and if `isEndOfWord` is `true`.

3. **Prefix Search (`startsWith` function)**
   - Checks if a prefix exists in the trie.

### **Output**

```
Search 'apple': Found
Search 'app': Found
Prefix 'ap': Exists
Search 'banana': Not Found
```

### **Time Complexity**

| Operation    | Complexity |
| ------------ | ---------- |
| Insert       | **O(n)**   |
| Search       | **O(n)**   |
| Prefix Check | **O(n)**   |

Where **n** is the length of the word.  
Trie is useful for **dictionary-based searches, autocomplete, and spell checking**.

---

## **AVL Tree**

An **AVL Tree** (Adelson-Velsky and Landis Tree) is a **self-balancing Binary Search Tree (BST)** where the difference in height between the left and right subtrees (**balance factor**) of any node is at most **1**.

### **Properties of AVL Tree**

✅ **Height-balanced:** The height difference between left and right subtrees is **≤ 1**.  
✅ **Self-balancing:** After insertion or deletion, rotations are performed to maintain balance.  
✅ **Faster operations:** Search, insert, and delete operations take **O(log n)** time.

### **Rotations in AVL Tree**

To maintain balance, **four types of rotations** are used:

1. **Right Rotation (RR)**
2. **Left Rotation (LL)**
3. **Left-Right Rotation (LR)**
4. **Right-Left Rotation (RL)**

> Ignore implementation if you have less time

### **C++ Implementation of AVL Tree**

```cpp
#include <iostream>
using namespace std;

// AVL Tree Node
class Node {
public:
    int data;
    Node* left;
    Node* right;
    int height;

    Node(int value) {
        data = value;
        left = right = nullptr;
        height = 1; // New node is initially at height 1
    }
};

// Get height of the node
int getHeight(Node* node) {
    return node ? node->height : 0;
}

// Get balance factor
int getBalanceFactor(Node* node) {
    return node ? getHeight(node->left) - getHeight(node->right) : 0;
}

// Right Rotate (LL Rotation)
Node* rightRotate(Node* y) {
    Node* x = y->left;
    Node* T2 = x->right;

    // Perform rotation
    x->right = y;
    y->left = T2;

    // Update heights
    y->height = max(getHeight(y->left), getHeight(y->right)) + 1;
    x->height = max(getHeight(x->left), getHeight(x->right)) + 1;

    return x; // New root
}

// Left Rotate (RR Rotation)
Node* leftRotate(Node* x) {
    Node* y = x->right;
    Node* T2 = y->left;

    // Perform rotation
    y->left = x;
    x->right = T2;

    // Update heights
    x->height = max(getHeight(x->left), getHeight(x->right)) + 1;
    y->height = max(getHeight(y->left), getHeight(y->right)) + 1;

    return y; // New root
}

// Insert a node in AVL Tree
Node* insert(Node* root, int value) {
    if (!root)
        return new Node(value);

    if (value < root->data)
        root->left = insert(root->left, value);
    else if (value > root->data)
        root->right = insert(root->right, value);
    else
        return root; // Duplicates not allowed

    // Update height
    root->height = max(getHeight(root->left), getHeight(root->right)) + 1;

    // Get balance factor
    int balance = getBalanceFactor(root);

    // Perform rotations if unbalanced
    // Left Heavy (LL)
    if (balance > 1 && value < root->left->data)
        return rightRotate(root);

    // Right Heavy (RR)
    if (balance < -1 && value > root->right->data)
        return leftRotate(root);

    // Left-Right (LR)
    if (balance > 1 && value > root->left->data) {
        root->left = leftRotate(root->left);
        return rightRotate(root);
    }

    // Right-Left (RL)
    if (balance < -1 && value < root->right->data) {
        root->right = rightRotate(root->right);
        return leftRotate(root);
    }

    return root; // No rotations needed
}

// Find the node with the smallest value (used in deletion)
Node* minValueNode(Node* node) {
    Node* current = node;
    while (current->left)
        current = current->left;
    return current;
}

// Delete a node in AVL Tree
Node* deleteNode(Node* root, int value) {
    if (!root)
        return root;

    if (value < root->data)
        root->left = deleteNode(root->left, value);
    else if (value > root->data)
        root->right = deleteNode(root->right, value);
    else {
        // Node with one or no child
        if (!root->left || !root->right) {
            Node* temp = root->left ? root->left : root->right;
            if (!temp) { // No child case
                temp = root;
                root = nullptr;
            } else
                *root = *temp; // One child case
            delete temp;
        } else {
            // Node with two children: Get inorder successor
            Node* temp = minValueNode(root->right);
            root->data = temp->data;
            root->right = deleteNode(root->right, temp->data);
        }
    }

    if (!root) return root;

    // Update height
    root->height = max(getHeight(root->left), getHeight(root->right)) + 1;

    // Get balance factor
    int balance = getBalanceFactor(root);

    // Perform rotations if unbalanced
    if (balance > 1 && getBalanceFactor(root->left) >= 0)
        return rightRotate(root);

    if (balance > 1 && getBalanceFactor(root->left) < 0) {
        root->left = leftRotate(root->left);
        return rightRotate(root);
    }

    if (balance < -1 && getBalanceFactor(root->right) <= 0)
        return leftRotate(root);

    if (balance < -1 && getBalanceFactor(root->right) > 0) {
        root->right = rightRotate(root->right);
        return leftRotate(root);
    }

    return root;
}

// Search in AVL Tree
bool search(Node* root, int key) {
    if (!root)
        return false;
    if (root->data == key)
        return true;
    if (key < root->data)
        return search(root->left, key);
    return search(root->right, key);
}

// In-order traversal (sorted order)
void inorder(Node* root) {
    if (root) {
        inorder(root->left);
        cout << root->data << " ";
        inorder(root->right);
    }
}

// Driver Code
int main() {
    Node* root = nullptr;

    // Insert values
    root = insert(root, 30);
    root = insert(root, 20);
    root = insert(root, 40);
    root = insert(root, 10);
    root = insert(root, 25);
    root = insert(root, 35);
    root = insert(root, 50);

    cout << "In-order Traversal (Sorted): ";
    inorder(root);
    cout << endl;

    // Search
    cout << "Search 25: " << (search(root, 25) ? "Found" : "Not Found") << endl;

    // Delete a node
    root = deleteNode(root, 40);
    cout << "After Deleting 40: ";
    inorder(root);
    cout << endl;

    return 0;
}
```

### **Operations & Complexity**

| Operation | Complexity   |
| --------- | ------------ |
| Insertion | **O(log n)** |
| Deletion  | **O(log n)** |
| Search    | **O(log n)** |

### **Example Output**

```
In-order Traversal (Sorted): 10 20 25 30 35 40 50
Search 25: Found
After Deleting 40: 10 20 25 30 35 50
```

### **Summary**

✅ **AVL Trees** are height-balanced **BSTs**.  
✅ **Rotations** (LL, RR, LR, RL) ensure balance.  
✅ **Operations take O(log n) time** for insert, delete, and search.

---

## **M-Way Tree**

An **M-way tree** (also called an **M-ary tree**) is a **generalized tree** where each node can have **at most M children** (instead of just 2 like in a binary tree).

### **Key Properties of M-Way Trees**

✅ **Each node has up to M children.**  
✅ **Each node stores up to (M-1) keys (in case of search trees).**  
✅ **M-Way Trees are often used in databases, file systems, and indexing structures.**  
✅ **Special cases include:**

- **Binary Tree (M = 2)**
- **Ternary Tree (M = 3)**
- **B-Tree (M varies, used in databases)**

### **Types of M-Way Trees**

1. **General M-Way Tree**

   - Each node has at most M children, but no strict rule on ordering.

2. **M-Way Search Tree**
   - An ordered M-way tree where:
     - Keys in each node are sorted.
     - Children pointers separate ranges of keys.
     - Example: B-Trees, B+ Trees (used in databases).

### **Operations on M-Way Trees**

1. **Insertion**

   - Insert keys in sorted order in a node.
   - If a node overflows (more than M-1 keys), it **splits** (common in B-Trees).

2. **Search**

   - Check the keys in a node.
   - If the key isn't found, move to the appropriate child based on key range.
   - Complexity: **O(log n) for balanced M-Way trees**.

3. **Deletion**
   - Remove the key and adjust the tree.
   - If underflow occurs (too few keys), **merge** nodes or **borrow** from siblings.

### **Example of a 3-Way Search Tree (M = 3)**

```
        [ 10  30 ]
       /    |    \
    [ 5 ]  [15 25]  [35 40]
```

- **Keys are stored in ascending order.**
- **Child pointers direct to key ranges:**
  - Left subtree has keys **<10**
  - Middle subtree has keys **between 10 and 30**
  - Right subtree has keys **>30**

### **Use Cases of M-Way Trees**

✅ **Databases & Indexing:** B-Trees and B+ Trees are used in relational databases for indexing.  
✅ **File Systems:** Used in directories for fast file lookup (e.g., NTFS, ext4).  
✅ **Artificial Intelligence:** Decision trees in AI often use M-way structures.  
✅ **Trie Data Structures:** Tries (prefix trees) are special M-way trees used in text searching.

---

## **B+ Tree vs. B\* Tree**

### **1. What is a B+ Tree?**

A **B+ Tree** is a **self-balancing M-way search tree** commonly used in **databases and file systems**. It extends the **B-Tree** by storing **all data in leaf nodes**, while internal nodes only store keys for navigation.

#### **Properties of B+ Tree**

✅ **Internal nodes store only keys** (used for indexing).  
✅ **Leaf nodes store actual records (data)**.  
✅ **All leaf nodes are linked in a linked list** (fast range queries).  
✅ **Every node (except root) has at least ⌈M/2⌉ children (ensuring balance).**

**Example of a B+ Tree (M = 3)**

```
         [ 30 60 ]
        /    |    \
   [10 20]  [30 50]  [60 80]
```

- Internal nodes **[30, 60]** store **only keys**.
- Leaf nodes **[10, 20]**, **[30, 50]**, **[60, 80]** store **actual data**.
- Leaf nodes are linked for fast traversal.

### **2. What is a B\* Tree?**

A **B\* Tree** is an **optimized version of a B+ Tree** with better space utilization and fewer splits. It ensures that nodes are at **least 2/3 full** before splitting, compared to **1/2 full in B+ Trees**.

#### **Properties of B\* Tree**

✅ **Requires nodes to be at least 2/3 full (instead of 1/2 in B+ Tree).**  
✅ **Uses sibling redistribution before splitting a node.**  
✅ **Fewer node splits, leading to a more compact structure.**

**Example of a B\* Tree (M = 3)**

```
        [ 30 60 ]
       /    |    \
   [10 20] [30 40 50] [60 70 80]
```

- More **compact** than a B+ Tree, with **denser nodes**.

### **3. Differences Between B+ Tree and B\* Tree**

| Feature           | **B+ Tree**                                           | **B\* Tree**                               |
| ----------------- | ----------------------------------------------------- | ------------------------------------------ |
| **Storage**       | Internal nodes store only keys, data is in leaf nodes | Same as B+ Tree                            |
| **Node Filling**  | Nodes are at least **50% full**                       | Nodes are at least **66% full**            |
| **Splitting**     | A node splits when it’s 100% full                     | Uses **redistribution first**, then splits |
| **Performance**   | Slightly more splits, more nodes                      | Fewer splits, better space usage           |
| **Range Queries** | Very fast (linked leaf nodes)                         | Same as B+ Tree                            |
| **Best for**      | Databases, indexing                                   | High-performance databases, file systems   |

### **4. Where and When Are They Used?**

#### ✅ **B+ Tree Applications**

1. **Database Indexing (Relational Databases, MySQL, PostgreSQL, Oracle)**

   - Used for indexing to enable fast **search, insert, delete** operations.
   - Example: MySQL **InnoDB** storage engine uses B+ Trees for indexing.

2. **File Systems (NTFS, ext4, HFS+, ReiserFS, XFS)**

   - Used for **directory structures** to enable fast **file lookups**.
   - Example: **NTFS (Windows file system)** uses a B+ Tree for file metadata.

3. **Key-Value Stores (RocksDB, LevelDB)**
   - **NoSQL databases** use B+ Trees for efficient key-value storage.

#### ✅ **B\* Tree Applications**

1. **High-Performance Database Indexing**

   - Used in situations requiring **fewer splits** and **better memory utilization**.

2. **File Systems with High Space Utilization**
   - Example: **HFS+ (Mac OS file system)** uses **B\* Trees** for metadata storage.

### **5. When to Use B+ Tree vs. B\* Tree?**

| Scenario                      | Use **B+ Tree** | Use **B\* Tree** |
| ----------------------------- | --------------- | ---------------- |
| **General database indexing** | ✅ Yes          | ❌ No            |
| **File system directories**   | ✅ Yes          | ✅ Yes           |
| **Low-memory environments**   | ❌ No           | ✅ Yes           |
| **Faster lookup performance** | ✅ Yes          | ✅ Yes           |
| **Faster insert/delete**      | ✅ Yes          | ❌ No            |
| **Better space utilization**  | ❌ No           | ✅ Yes           |

### **Summary**

1. **B+ Trees** are widely used in **databases and file systems**.
2. **B\* Trees** are an **optimized version** of B+ Trees with **better space efficiency**.
3. **B+ Trees split nodes more often**, while **B\* Trees redistribute first** before splitting.
4. **Both are used in databases, file systems, and indexing systems** for efficient searching.

---

## **Heaps: Structural Properties, Heapify, and Heap Sort**

### **What is a Heap?**

A **Heap** is a **complete binary tree** that satisfies the **heap property**. Heaps are mainly used for **priority queues, scheduling, and sorting algorithms**.

### **Structural Properties of Heaps**

✅ **Complete Binary Tree**:

- Every level is **fully filled**, except possibly the last level, which is filled from **left to right**.  
  ✅ **Heap Property**:
- **Max Heap**: Parent node is **greater than or equal to** its children.
- **Min Heap**: Parent node is **smaller than or equal to** its children.

#### **Max Heap Example**

```
        50
       /  \
     30    40
    /  \   /
   10  20 15
```

✅ **Parent ≥ Children** (Max Heap property holds).

#### **Min Heap Example**

```
        10
       /  \
     30    40
    /  \   /
   50  20 15
```

✅ **Parent ≤ Children** (Min Heap property holds).

### **Heapify: Converting an Unordered Tree into a Heap**

**Heapify** is a process to maintain the **heap property** by adjusting nodes.

- **Time Complexity**: **O(log n)** for a single node.
- **Types of Heapify**:
  1. **Max-Heapify**: Ensures the max heap property.
  2. **Min-Heapify**: Ensures the min heap property.

#### **Algorithm for Heapify**

1. Check if the parent violates the heap property.
2. If violated, **swap** with the **largest (Max Heap) or smallest (Min Heap) child**.
3. Recursively apply heapify down the tree.

#### **Heapify Code in C++**

```cpp
void heapify(int arr[], int n, int i) {
    int largest = i;      // Assume root is largest
    int left = 2 * i + 1; // Left child
    int right = 2 * i + 2; // Right child

    // If left child is larger than root
    if (left < n && arr[left] > arr[largest])
        largest = left;

    // If right child is larger than largest so far
    if (right < n && arr[right] > arr[largest])
        largest = right;

    // If largest is not root
    if (largest != i) {
        swap(arr[i], arr[largest]); // Swap
        heapify(arr, n, largest);   // Recursively heapify the affected subtree
    }
}
```

### **4. Heap Sort: Sorting Using Heap**

**Heap Sort** is a **comparison-based sorting algorithm** that uses a **heap structure** to sort elements.

- **Time Complexity**: **O(n log n)**
- **Space Complexity**: **O(1) (in-place sorting)**
- **Stable Sort?** ❌ No

#### **Steps of Heap Sort**

1. **Build a max heap** from the array (**O(n)**).
2. Swap the root (largest element) with the last element.
3. Reduce the heap size and **heapify** the root (**O(log n)**).
4. Repeat until the heap is empty.

#### **Heap Sort Code in C++**

```cpp
#include <iostream>
using namespace std;

// Heapify function to maintain max heap property
void heapify(int arr[], int n, int i) {
    int largest = i;      // Root
    int left = 2 * i + 1; // Left child
    int right = 2 * i + 2; // Right child

    // Check if left child is larger
    if (left < n && arr[left] > arr[largest])
        largest = left;

    // Check if right child is larger
    if (right < n && arr[right] > arr[largest])
        largest = right;

    // If largest is not root
    if (largest != i) {
        swap(arr[i], arr[largest]);  // Swap root with largest
        heapify(arr, n, largest);    // Recursively heapify
    }
}

// Function to perform Heap Sort
void heapSort(int arr[], int n) {
    // Build a max heap (Rearrange array)
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Extract elements from heap one by one
    for (int i = n - 1; i > 0; i--) {
        swap(arr[0], arr[i]); // Move current root to end
        heapify(arr, i, 0);   // Call heapify on reduced heap
    }
}

// Function to print array
void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

// Driver Code
int main() {
    int arr[] = {40, 10, 30, 50, 20, 60, 15};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArray(arr, n);

    heapSort(arr, n);

    cout << "Sorted array: ";
    printArray(arr, n);

    return 0;
}
```

#### **Output:**

```
Original array: 40 10 30 50 20 60 15
Sorted array: 10 15 20 30 40 50 60
```

### **5. Time & Space Complexity Comparison**

| Algorithm | **Best Case**  | **Average Case** | **Worst Case** | **Space Complexity** |
| --------- | -------------- | ---------------- | -------------- | -------------------- |
| Heap Sort | **O(n log n)** | **O(n log n)**   | **O(n log n)** | **O(1) (In-place)**  |

### **6. Applications of Heaps**

✅ **Priority Queues** (Dijkstra’s Algorithm, Task Scheduling)  
✅ **Heap Sort** (Efficient sorting in limited space)  
✅ **Graph Algorithms** (Prim’s, Dijkstra’s Shortest Path)  
✅ **Memory Management** (Heap Memory Allocation)  
✅ **Operating Systems** (Job Scheduling, Load Balancing)

### **Advantages of Heap Sort**

✅ **Efficient for large datasets** (O(n log n)).  
✅ **Does not require extra space** (unlike Merge Sort).  
✅ **Good for Priority Queues (fast insert/delete).**

### **Disadvantages of Heap Sort**

❌ **Not a stable sort** (may not preserve order of equal elements).  
❌ **More swaps compared to Quick Sort**, making it slower for some cases.

### **Summary**

1. **Heaps are complete binary trees** that follow the **heap property** (Max or Min Heap).
2. **Heapify** maintains the heap structure in **O(log n)** time.
3. **Heap Sort is an efficient O(n log n) sorting algorithm** using the heap data structure.
4. **Heaps are widely used** in **priority queues, graph algorithms, and scheduling systems**.

---

## Priority Queue

```cpp
#include <iostream>
#include <vector>
using namespace std;

class PriorityQueue
{
    vector<int> pq;

public:
    PriorityQueue(){}

    bool isEmpty()
    {
        return pq.size() == 0;
    }

    int getSize()
    {
        return pq.size();
    }

    int getMin()
    {
        if (pq.size() == 0)
            return 0; // Priority Queue is empty;

        return pq[0];
    }

private:
    void swap(vector<int> &pq, int pI, int cI)
    {
        int x = pq[pI];
        pq[pI] = pq[cI];
        pq[cI] = x;
    }

public:
    void insert(int data)
    {
        pq.push_back(data);
        int childIndex = pq.size() - 1;
        // I can't check with parent
        // So I have to check with children after they inserted;

        while (childIndex > 0)
        {
            int parentIndex = (childIndex - 1) / 2;
            if (pq[childIndex] < pq[parentIndex])
                swap(pq, parentIndex, childIndex);
            else
                break;
            childIndex = parentIndex;
        }
    }

    int remove()
    {
        if (pq.size() == 0)
        {
            cout << "Priority Queue is empty" << endl;
            return 0;
        }

        int ans = pq[0];
        int last = pq.size() - 1;
        pq[0] = pq[last];
        pq.pop_back();

        int parentIndex = 0;
        int leftChildIndex = (2 * parentIndex) + 1;
        int rightChildIndex = (2 * parentIndex) + 2;

        // leftChildIndex and rightChildIndex must in limits because if they are
        // not in limits then I am accessing the garbage(wrong) value
        // or memory which is not allocated to me So be care of this

        while (leftChildIndex < pq.size())
        {
            int minIndex = parentIndex;
            if (pq[leftChildIndex] < pq[minIndex])
                minIndex = leftChildIndex;
            if (rightChildIndex < pq.size() && pq[rightChildIndex] < pq[minIndex])
                minIndex = rightChildIndex;
            if (minIndex == parentIndex)
                break;

            swap(pq, parentIndex, minIndex);
            parentIndex = minIndex;
            leftChildIndex = (2 * parentIndex) + 1;
            rightChildIndex = (2 * parentIndex) + 2;
        }

        return ans;
    }
};


int main()
{
    PriorityQueue pq;
    for (int i = 10; i >= 0; i--)
        pq.insert(i);

    cout << "Size : " << pq.getSize() << endl;
    cout << "Empty : " << pq.isEmpty() << endl;
    while (!pq.isEmpty())
    {
        // cout << "Min : " << pq.getMin() << endl;
        // cout << "Remove : " << pq.remove() << endl;
        cout << pq.remove() << " ";
    }

    return 0;
}
```

---

## **`Gagan Saini`**
