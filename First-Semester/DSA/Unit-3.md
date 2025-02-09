# Unit-3

## Linked List

### Structure

```cpp
class Node
{
public:
    int data;
    Node *next;

    Node(int data)
    {
        this->data = data;
        this->next = NULL;
    }
};
```

### Take Input

```cpp
Node *takeInput()
{
    int data;
    cin >> data;

    Node *head = NULL;
    Node *temp = head;
    while (data != -1)
    {
        Node *newNode = new Node(data);
        if (head == NULL)
        {
            head = newNode;
            temp = head;
        }
        else
        {
            temp->next = newNode;
            temp = temp->next;
        }
        cin >> data;
    }

    return head;
}
```

### Print LL

```cpp
void print(Node *head)
{
    Node *temp = head;
    while (temp != NULL)
    {
        cout << temp->data << " ";
        temp = temp->next;
    }
    cout << endl;
}
```

### Length of LL

1. **Iterative Method**

```cpp
int length(Node* head){
    int count = 0;
    Node* temp = head;

    while(temp != NULL){
        temp = temp->next;
        count++;
    }

    return count;
}
```

2. **Recursive Method**

```cpp
int length(Node* head){
    if(head == NULL){
        // Base case length is 0;
        return 0;
    }

    return length(head->next)+1;
}
```

### Insert in LL

1. **Iterative Method**

```cpp
Node* insertData(Node* head, int pos, int data){
    Node* newNode = new Node(data);

    if(pos == 0){
        // Insert at head
        newNode->next = head;
        return newNode;
    }

    Node* temp = head;
    int count = 0;
    while(count<pos-1 && temp != NULL){
        // Loop till position element;
        count++;
        temp = temp->next;
    }

    newNode->next = temp->next;
    temp->next = newNode;
    return head;
}
```

2. **Recursive Method**

```cpp
Node* insertRecursively(Node* head,int pos, int data){
    Node* temp = head;
    if(pos == 0){
        Node* newNode = new Node(data);
        newNode->next = temp;
        temp = newNode;

        return temp;
    }
    temp = temp->next;
    Node* x = insertRecursively(temp, pos-1, data);
    head->next = x;

    return head;
}
```

### Delete in LL

1. **Iterative Method**

```cpp
Node* deleteData(Node* head, int pos){
    if(pos == 0){
        // Delete from head;
        Node* temp = head;
        head = head->next;

        delete temp;
        return head;
    }

    Node* temp = head;
    int count = 0;
    while(count<pos-1 && temp != NULL){
        count++;
        temp = temp->next;
    }

    Node* x = temp->next;
    Node* y = x->next;

    delete x;
    temp->next = y;

    return head;
}
```

2. **Recursive Method**

```cpp
Node* deleteRecursively(Node* head, int pos){
    Node* temp = head;
    if(pos == 0){
        head = head->next;
        delete temp;

        return head;
    }
    temp = temp->next;
    Node* x = deleteRecursively(temp, pos-1);
    head->next = x;

    return head;
}
```

### Mid Point

1. **Length/2 Method**

```cpp
Node* midPoint(Node* head) {
    if (!head) return nullptr; // Empty list

    int lengthLL = length(head);
    int mid = lengthLL / 2;

    Node* temp = head;

    for (int i = 0; i < mid; i++) {
        temp = temp->next;
    }

    return temp;
}
```

2. **Slow & Fast Method (Hear & Tortoise Method)**

```cpp
int midPoint(Node* head){
    Node* slow = head;
    Node* fast = head->next;

    while(fast != NULL && fast->next != NULL){
        slow = slow->next;
        fast = fast->next->next;
    }

    return slow->data;
}
```

### Reverse LL

1. **Recursive Method**

Time Complexity (TC) → `O(N*N)`
Space Complexity (SC) → `O(N)` → Recursive Space

```cpp
Node *reverseLL1(Node *head)
{
    if (head == NULL || head->next == NULL)
        return head;

    Node *smallAns = reverseLL1(head->next);
    Node *temp = smallAns;

    while (temp->next != NULL)
        temp = temp->next;

    temp->next = head;
    head->next = NULL;

    return smallAns;
}
```

2. **Recursive Method with Pair**

```cpp
class Pair
{
    public:
        Node *head;
        Node *tail;
};

Pair reverseLL2(Node *head)
{
    if (head == NULL || head->next == NULL)
    {
        Pair ans;
        ans.head = head;
        ans.tail = head;

        return ans;
    }

    Pair smallAns = reverseLL2(head->next);
    smallAns.tail->next = head;
    head->next = NULL;

    Pair ans;
    ans.head = smallAns.head;
    ans.tail = head;

    return ans;
}

Node *reverseLL2_call(Node *head)
{
    return reverseLL2(head).head;
}
```

3. **Recursive Method (Most Effective)**

```cpp
Node *reverseLL3(Node *head)
{
    if (head == NULL || head->next == NULL)
        return head;

    Node *smallAns = reverseLL3(head->next);
    Node *tail = head->next;
    tail->next = head;

    head->next = NULL;
    return smallAns;
}
```

4. **Iterative Method**

```cpp
Node *reverseLL4(Node *head)
{
    Node *prev = NULL;
    Node *n = head->next;
    Node *curr = head;

    while (curr != NULL)
    {
        curr->next = prev;
        prev = curr;
        curr = n;

        if (curr == NULL)
        {
            return prev;
        }
        if (n == NULL)
        {
            // Because if I don't do that then I am trying to access NULL->next and it gives me segmantion fault;
            return prev;
        }
        n = n->next;
    }

    return prev;
}

```

---

## Doubly Linked List

### Structure

```cpp
class Node{
    public:
    int data;
    Node* next;
    Node* prev;

    Node(int data){
        this->data = data;
        this->next = NULL;
        this->prev = NULL;
    }
};
```

### Take Input

```cpp
Node* takeInput(){
    int data;
    cin>>data;

    Node* head = NULL;
    Node* temp = head;
    Node* prev = head;

    while(data != -1){
        Node* newNode = new Node(data);
        if(head == NULL){
            head = newNode;
            temp = head;
        }
        else{
            temp->next = newNode;
            newNode->prev = temp;
            temp = temp->next;
        }
        cin>>data;
    }

    return head;
}
```

### Print

```cpp
void print(Node* head){
    Node* temp = head;
    while(temp->next != NULL){
        cout<<temp->data<<" ";
        temp = temp->next;
    }
    cout<<temp->data;
    cout<<endl;

    while(temp->prev != NULL){
        cout<<temp->data<<" ";
        temp = temp->prev;
    }
    cout<<temp->data;
    temp = temp->prev;
    cout<<endl;

}
```

---

## Application of Polynomial Arithmetic

Polynomial arithmetic involves operations like addition, subtraction, and multiplication on polynomials. These operations can be efficiently implemented using **linked lists**, as each term in the polynomial can be represented as a node in the list.

### **Why Use Linked Lists for Polynomial Arithmetic?**

1. **Dynamic Memory Allocation** – Linked lists allow efficient memory usage by allocating space only for non-zero terms.
2. **Easy Insertion & Deletion** – Polynomial terms can be easily added or removed without shifting elements (as in arrays).
3. **Efficient Polynomial Operations** – Addition, subtraction, and multiplication can be performed efficiently by traversing the linked lists.

### **Applications of Polynomial Arithmetic Using Linked Lists**

1. **Symbolic Computation Systems**
   - Used in **computer algebra systems** (CAS) like MATLAB, Mathematica, and SymPy to manipulate algebraic expressions.
2. **Scientific Computing & Engineering Simulations**

   - Polynomial approximations are widely used in **numerical methods**, **physics simulations**, and **engineering applications**.

3. **Cryptography & Error-Correcting Codes**

   - Polynomial arithmetic is used in **finite field operations** in cryptography (RSA, ECC, etc.) and **error-detecting/correcting codes** like CRC (Cyclic Redundancy Check).

4. **Control Systems & Signal Processing**

   - Transfer functions in **control theory** are often represented as polynomials, requiring addition, multiplication, and differentiation.

5. **Machine Learning & AI**
   - Polynomial regression in machine learning relies on polynomial manipulation to fit curves to data points.

### **Implementation of Polynomial Arithmetic Using Linked List in C++**

```cpp
#include <iostream>
using namespace std;

class Node {
    int coeff;
    int power;
    Node* next;

    Node(int c, int p){
        coeff = c;
        power = p;
        next = nullptr;
    }
};

void insert(Node*& head, int coeff, int power) {
    Node* newNode = new Node(coeff, power);
    if (!head || head->power < power) {
        newNode->next = head;
        head = newNode;
        return;
    }

    Node* temp = head;
    while (temp->next && temp->next->power >= power)
        temp = temp->next;

    if (temp->power == power) {
        temp->coeff += coeff;
    } else {
        newNode->next = temp->next;
        temp->next = newNode;
    }
}

void printPolynomial(Node* head) {
    while (head) {
        cout << head->coeff << "x^" << head->power;
        if (head->next) cout << " + ";
        head = head->next;
    }
    cout << endl;
}

Node* addPolynomials(Node* poly1, Node* poly2) {
    Node* result = nullptr;

    while (poly1 || poly2) {
        if (!poly1) {
            insert(result, poly2->coeff, poly2->power);
            poly2 = poly2->next;
        } else if (!poly2) {
            insert(result, poly1->coeff, poly1->power);
            poly1 = poly1->next;
        } else if (poly1->power > poly2->power) {
            insert(result, poly1->coeff, poly1->power);
            poly1 = poly1->next;
        } else if (poly1->power < poly2->power) {
            insert(result, poly2->coeff, poly2->power);
            poly2 = poly2->next;
        } else {
            insert(result, poly1->coeff + poly2->coeff, poly1->power);
            poly1 = poly1->next;
            poly2 = poly2->next;
        }
    }

    return result;
}

int main() {
    Node* poly1 = nullptr;
    Node* poly2 = nullptr;

    insert(poly1, 3, 2); // 3x^2
    insert(poly1, 5, 1); // 5x^1
    insert(poly1, 2, 0); // 2x^0

    insert(poly2, 4, 2); // 4x^2
    insert(poly2, -2, 1); // -2x^1
    insert(poly2, 1, 0); // 1x^0

    cout << "Polynomial 1: ";
    printPolynomial(poly1);

    cout << "Polynomial 2: ";
    printPolynomial(poly2);

    Node* sum = addPolynomials(poly1, poly2);
    cout << "Sum: ";
    printPolynomial(sum);

    return 0;
}
```

### **Explanation**

- **Insertion**: Inserts polynomial terms in descending order of power.
- **Addition**: Merges terms with the same exponent and adds their coefficients.
- **Output Example**:
  ```
  Polynomial 1: 3x^2 + 5x^1 + 2x^0
  Polynomial 2: 4x^2 + -2x^1 + 1x^0
  Sum: 7x^2 + 3x^1 + 3x^0
  ```

### **Conclusion**

- **Linked lists** are ideal for **polynomial arithmetic** due to their flexibility.
- Used in **scientific computing, cryptography, machine learning, and engineering simulations**.
- Supports **efficient insertion, deletion, and merging of terms**.

---

## Stack

1. **Using Array**

```cpp
#include <iostream>
using namespace std;

template <typename T>
class StackUsingArray
{
    T *data;
    int nextIndex, capacity;

public:
    StackUsingArray()
    {
        data = new T[2];
        nextIndex = 0;
        capacity = 2;
    }

    bool isEmpty()
    {
        return nextIndex == 0;
    }

    void push(T x)
    {
        if (nextIndex == capacity)
        {
            T *newData = new T[2 * capacity];
            for (int i = 0; i < capacity; i++)
            {
                newData[i] = data[i];
            }
            capacity *= 2;
            delete[] data;
            data = newData;
        }
        data[nextIndex] = x;
        nextIndex++;
    }

    T pop()
    {
        if (isEmpty())
        {
            cout << "Stack is alreay empty ";
            return INT16_MIN;
        }
        nextIndex--;
        return data[nextIndex];
    }

    T top()
    {
        if (isEmpty())
        {
            cout << "Stack is alreay empty ";
            return INT16_MIN;
        }
        return data[nextIndex - 1];
    }
};
```

↳ How to use

```cpp
int main()
{
    StackUsingArray<int> s;
    s.push(10);
    s.push(20);
    s.push(30);
    s.push(40);
    s.push(50);

    cout << "isEmpty " << s.isEmpty() << endl;
    cout << "top " << s.top() << endl;

    while (!s.isEmpty())
    {
        cout << s.pop() << " ";
    }
    cout << endl;

    cout << s.top() << endl;
    return 0;
}
```

2. **Using Linked List**

```cpp
#include <iostream>
using namespace std;

template <typename T>
class Node
{
public:
    T data;
    Node<T> *next;

    Node(T data)
    {
        this->data = data;
        next = NULL;
    }
};

template <typename T>
class StackUsingLL
{
    Node<T> *head;
    int size;

public:
    StackUsingLL()
    {
        head = NULL;
        size = 0;
    }

    int getSize()
    {
        return size;
    }

    void push(T data)
    {
        Node<T> *newNode = new Node<T>(data);
        newNode->next = head;
        head = newNode;

        size++;
    }

    T pop()
    {
        if (head == NULL)
        {
            cout << "Stack is empty ";
            return 0;
        }

        Node<T> *temp = head;
        head = head->next;
        T ans = temp->data;
        delete temp;
        size--;

        return ans;
    }

    T top()
    {
        if (head == NULL)
        {
            cout << "Stack is empty ";
            return 0;
        }
        return head->data;
    }

    bool isEmpty()
    {
        return size == 0;
    }

    int getMinimum()
    {
        if (head == NULL)
        {
            cout << "Stack is empty ";
            return INT16_MIN;
        }

        Node<T> *temp = head;
        int min = INT16_MAX;

        while (temp != NULL)
        {
            if (temp->data < min)
            {
                min = temp->data;
            }
            temp = temp->next;
        }

        return min;
    }

    int getMaximum()
    {
        if (head == NULL)
        {
            cout << "Stack is empty ";
            return INT16_MIN;
        }

        Node<T> *temp = head;
        int max = INT16_MIN;

        while (temp != NULL)
        {
            if (temp->data > max)
            {
                max = temp->data;
            }
            temp = temp->next;
        }

        return max;
    }
};
```

↳ How to use

```cpp
int main()
{

    StackUsingLL<int> s;
    s.push(10);
    s.push(20);
    s.push(30);
    s.push(40);
    s.push(50);
    s.push(60);
    s.push(70);

    cout << s.top() << endl;
    cout << s.isEmpty() << endl;
    cout << s.getSize() << endl;
    cout << s.getMinimum() << endl;
    cout << s.getMaximum() << endl;

    while (s.getSize())
    {
        cout << s.pop() << " ";
    }
    cout << endl;

    return 0;
}
```

### Balanced Parathensis Question

```cpp
#include <iostream>
#include "StackUsingLL.h"
using namespace std;

int main()
{
    StackUsingLL<char> st;
    string str;
    cin >> str;

    int i = 0;
    while (str[i] != '\0')
    {
        if (str[i] == '(' || str[i] == '[' || str[i] == '{')
        {
            st.push(str[i]);
        }
        else
        {
            if (st.getSize() == 0)
                break;

            if (st.top() == '(' && str[i] == ')')
                st.pop();
            else if (st.top() == '{' && str[i] == '}')
                st.pop();
            else if (st.top() == '[' && str[i] == ']')
                st.pop();
            else
                break;
        }
        i++;
    }

    if (st.getSize() == 0)
        cout << "Balanced" << endl;
    else
        cout << "Not Balanced" << endl;

    return 0;
}
```

---

## Queue

1. **Using Array**

```cpp
#include <iostream>
using namespace std;

template <typename T>
class QueueUsingArray
{
    T *data;
    int nextIndex, firstIndex, size;
    int capacity;

public:
    QueueUsingArray()
    {
        data = new T[4];
        nextIndex = 0;
        firstIndex = -1;
        size = 0;
        capacity = 4;
    }

    int getSize()
    {
        return size;
    }

    bool isEmpty()
    {
        return size == 0;
    }

    void enqueue(T element)
    {
        if (size == capacity)
        {
            int j = 0;
            T *newData = new T[2 * capacity];
            for (int i = firstIndex; i < capacity; i++)
            {
                newData[j++] = data[i];
            }

            for (int i = 0; i < firstIndex; i++)
            {
                newData[j++] = data[i];
            }

            delete[] data;
            data = newData;
            nextIndex = capacity;
            firstIndex = 0;
            capacity *= 2;
        }
        data[nextIndex] = element;
        nextIndex = (nextIndex + 1) % capacity;
        if (firstIndex == -1)
        {
            firstIndex = 0;
        }
        size++;
    }

    T dequeue()
    {
        if (firstIndex == -1 || size == 0)
        {
            cout << "Queue is empty" << endl;
            firstIndex = -1;
            nextIndex = 0;
            return 0;
        }
        T ans = data[firstIndex];
        firstIndex = (firstIndex + 1) % capacity;
        size--;
        return ans;
    }

    T front()
    {
        if (firstIndex == -1)
        {
            cout << "Queue is empty" << endl;
            return 0;
        }
        return data[firstIndex];
    }
};
```

↳ How to use

```cpp
#include <iostream>
#include "QueueUsingArray.h"
using namespace std;

int main()
{

    QueueUsingArray<int> q;
    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);
    q.enqueue(40);
    q.enqueue(50);
    q.enqueue(60);
    q.enqueue(70);
    q.enqueue(80);
    q.enqueue(90);
    q.enqueue(100);
    cout << q.getSize() << endl;
    cout << q.dequeue() << endl;
    cout << q.top() << endl;
    cout << q.getSize() << endl;
    cout << q.isEmpty() << endl;

    cout << q.front() << endl;
    cout << "Size = " << q.getSize() << endl;
    while (q.getSize())
    {
        cout << q.dequeue() << " ";
    }

    return 0;
}
```

2. **Using Linked List**

```cpp
#include <iostream>
using namespace std;

template <typename T>
class Node
{
public:
    T data;
    Node<T> *next;

    Node(T data)
    {
        this->data = data;
        next = NULL;
    }
};

template <typename T>
class QueueUsingLL
{
    Node<T> *head;
    Node<T> *temp;
    int size;

public:
    QueueUsingLL()
    {
        head = NULL;
        temp = NULL;
        size = 0;
    }

    int getSize()
    {
        return size;
    }

    bool isEmpty()
    {
        return size == 0;
    }

    // Insert at tail
    void enqueue(T element)
    {
        Node<T> *newNode = new Node<T>(element);
        if (head == NULL)
        {
            head = newNode;
            temp = newNode;
        }
        else
        {
            temp->next = newNode;
            temp = temp->next;
        }
        size++;
    }

    // Delete from head
    T dequeue()
    {
        if (size == 0)
        {
            head = NULL;
            cout << "Queue is empty!" << endl;
            return 0;
        }

        Node<T> *x = head;
        head = head->next;
        T ans = x->data;
        delete x;
        size--;
        return ans;
    }

    T front()
    {
        if (size == 0)
        {
            cout << "Queue is empty!" << endl;
            return 0;
        }

        return head->data;
    }

    T getMaximum()
    {
        int max = INT16_MIN;
        Node<T> *temp = head;
        while (temp != NULL)
        {
            if (temp->data > max)
            {
                max = temp->data;
            }
            temp = temp->next;
        }

        return max;
    }

    T getMinimum()
    {
        int min = INT16_MAX;
        Node<T> *temp = head;
        while (temp != NULL)
        {
            if (temp->data < min)
            {
                min = temp->data;
            }
            temp = temp->next;
        }

        return min;
    }
};
```

↳ How to use

```cpp
#include <iostream>
#include "QueueUsingLL.h"
using namespace std;

int main()
{
    QueueUsingLL<int> q;
    for (int i = 10; i <= 90; i += 10)
        q.enqueue(i);

    cout << q.front() << endl;      // -> 10
    cout << q.getSize() << endl;    // -> 9
    cout << q.isEmpty() << endl;    // -> 0(false)
    cout << q.getMaximum() << endl; // -> 90
    cout << q.getMinimum() << endl; // -> 10

    while (q.getSize())
        cout << q.dequeue() << " ";

    cout << endl;
    cout << q.front() << endl;   // -> Queue is empty!
    cout << q.getSize() << endl; // -> 0
    cout << q.isEmpty() << endl; // -> 1(true)

    return 0;
}
```

3. **Queue Using Stack**

```cpp
#include <iostream>
#include <stack>
using namespace std;

class Queue
{
    stack<int> input, output;

public:
    void enqueue(int x)
    {

        while (input.size() != 0)
        {
            int ans = input.top();
            input.pop();
            output.push(ans);
        }

        input.push(x);

        while (output.size() != 0)
        {
            int ans = output.top();
            output.pop();

            input.push(ans);
        }
    }

    int dequeue()
    {
        if (input.size() == 0)
        {
            return -1;
        }

        int ans = input.top();
        input.pop();

        return ans;
    }
};

int main()
{

    Queue q;
    q.enqueue(2);
    q.enqueue(3);

    cout << q.dequeue();
    return 0;
}
```

---

### Multi Stack & Multi Queue

In many applications, multiple stacks or queues are required within a single data structure to efficiently manage memory and optimize operations. These are called **Multi-Stack** and **Multi-Queue** implementations.

#### **1. Multi-Stack**

A **multi-stack** is a data structure where multiple stacks are implemented within a single array or memory block. This is useful when dealing with **multiple independent stack operations** without using multiple separate arrays.

**Implementation Approaches:**

1. **Fixed Division Method:**
   - The array is divided into `n` equal parts, each assigned to one stack.
   - Simple but may lead to wasted space if one stack is full and another is empty.
2. **Dynamic or Flexible Division Method:**
   - Uses dynamic partitioning to allocate space based on demand.
   - Allows stacks to expand or shrink based on usage.

#### **Applications:**

- **Multi-threaded applications** (handling different execution stacks).
- **Expression evaluation** (multiple operator precedence levels).
- **Memory management** (managing activation records in compilers).

### **2. Multi-Queue**

A **multi-queue** is a data structure where multiple queues are managed within a single array. It allows handling of **multiple queue-based tasks** efficiently in a shared memory structure.

**Implementation Approaches:**

1. **Fixed Partitioning:**

   - The array is divided into `n` equal segments, each acting as an independent queue.
   - Simple but can lead to memory underutilization.

2. **Circular Queue with Pointers:**

   - Uses a circular queue mechanism to allocate space dynamically.
   - More efficient in memory usage.

3. **Priority-based Queues:**
   - Multiple queues manage different priorities (e.g., CPU scheduling in OS).

#### **Applications:**

- **Operating Systems:** Multiple queues are used in scheduling algorithms (e.g., multi-level queues).
- **Networking:** Handling multiple message queues in communication systems.
- **Real-time Systems:** Managing tasks with different priorities.

### **Comparison Table:**

| Feature          | Multi-Stack                                               | Multi-Queue                                          |
| ---------------- | --------------------------------------------------------- | ---------------------------------------------------- |
| **Definition**   | Multiple stacks in a single array                         | Multiple queues in a single array                    |
| **Memory Usage** | Can be fixed or dynamic partitioning                      | Can be fixed or dynamic partitioning                 |
| **Operations**   | Push, Pop, Peek                                           | Enqueue, Dequeue, Peek                               |
| **Applications** | Expression evaluation, Memory management, Multi-threading | OS scheduling, Networking, Real-time task management |

---

## Polish Notation (PN) and Reverse Polish Notation (RPN)

### **1. What is Polish Notation (PN)?**

Also known as **Prefix Notation**, in Polish Notation, the operator is placed **before** its operands.

- Example:
  ```
  + 3 4  → (3 + 4)
  * + 3 4 5  → (3 + 4) * 5
  ```

### **2. What is Reverse Polish Notation (RPN)?**

Also known as **Postfix Notation**, in Reverse Polish Notation, the operator is placed **after** its operands.

- Example:
  ```
  3 4 +  → (3 + 4)
  3 4 + 5 *  → (3 + 4) * 5
  ```

### **Conversion Between PN and RPN**

To convert **Polish Notation (PN) → Reverse Polish Notation (RPN)** or vice versa, we follow **tree traversal techniques**.

**1. Polish Notation (Prefix) → Reverse Polish Notation (Postfix)**

#### **Steps:**

1. Construct an **expression tree** from the Prefix expression.
2. Perform a **postorder traversal** (Left-Right-Root) to get the Postfix expression.

**Example:**

**Prefix (PN):**

```
* + 3 4 5
```

**Expression Tree:**

```
       *
      / \
     +   5
    / \
   3   4
```

**Postorder Traversal (L-R-Root) → RPN (Postfix):**

```
3 4 + 5 *
```

**2. Reverse Polish Notation (Postfix) → Polish Notation (Prefix)**

#### **Steps:**

1. Construct an **expression tree** from the Postfix expression.
2. Perform a **preorder traversal** (Root-Left-Right) to get the Prefix expression.

**Example:**

**Postfix (RPN):**

```
3 4 + 5 *
```

**Expression Tree:**

```
       *
      / \
     +   5
    / \
   3   4
```

**Preorder Traversal (Root-L-R) → PN (Prefix):**

```
* + 3 4 5
```

### **C++ Program for Conversion**

Below is a C++ program that converts **Prefix to Postfix** and **Postfix to Prefix** using an **expression tree**.

> Don't need to read if you less time or don't want the implementation complexity.

```cpp
#include <iostream>
#include <stack>
#include <cctype>
using namespace std;

class Node {
    string data;
    Node *left, *right;

    Node(string val) : data(val), left(nullptr), right(nullptr) {}
};

bool isOperator(string s) {
    return (s == "+" || s == "-" || s == "*" || s == "/");
}

// Function to build an Expression Tree from Prefix (PN)
Node* constructFromPrefix(string prefix[], int &index, int n) {
    if (index >= n) return nullptr;

    Node* node = new Node(prefix[index]);
    index++;

    if (isOperator(node->data)) {
        node->left = constructFromPrefix(prefix, index, n);
        node->right = constructFromPrefix(prefix, index, n);
    }
    return node;
}

// Function to build an Expression Tree from Postfix (RPN)
Node* constructFromPostfix(string postfix[], int n) {
    stack<Node*> st;

    for (int i = 0; i < n; i++) {
        Node* node = new Node(postfix[i]);

        if (isOperator(postfix[i])) {
            node->right = st.top(); st.pop();
            node->left = st.top(); st.pop();
        }
        st.push(node);
    }
    return st.top();
}

void postorder(Node* root) {
    if (!root) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}

void preorder(Node* root) {
    if (!root) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}

int main() {
    // Prefix to Postfix Conversion
    string prefix[] = {"*", "+", "3", "4", "5"};
    int n1 = 5, index = 0;
    Node* root1 = constructFromPrefix(prefix, index, n1);

    cout << "Postfix Expression: ";
    postorder(root1);
    cout << endl;

    // Postfix to Prefix Conversion
    string postfix[] = {"3", "4", "+", "5", "*"};
    int n2 = 5;
    Node* root2 = constructFromPostfix(postfix, n2);

    cout << "Prefix Expression: ";
    preorder(root2);
    cout << endl;

    return 0;
}
```

### **Output:**

```
Postfix Expression: 3 4 + 5 *
Prefix Expression: * + 3 4 5
```

### **Conclusion**

- **Prefix → Postfix:** Use **postorder traversal** on an expression tree.
- **Postfix → Prefix:** Use **preorder traversal** on an expression tree.
- This approach ensures efficient and correct conversion between the two notations.

---

## **`Gagan Saini`**
