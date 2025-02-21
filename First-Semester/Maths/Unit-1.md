# Unit-1

## **Set Theory**

Set theory is a fundamental concept in mathematics that deals with collections of objects, called sets. Below are key concepts in set theory:

### **1. Sets and Elements**

A **set** is a well-defined collection of distinct objects, called **elements** or **members**. Sets are usually denoted by capital letters such as `A, B, C`, and elements by lowercase letters such as `a, b, c`.

- If an element `x` belongs to a set `A`, we write: `x∈A`
- If `x` does not belong to `A`, we write: `x∈/A` (This / is on the `∈` but able to write in notes)

### **Examples of Sets**

1. `A = { 1, 2, 3, 4 }` → A finite set with four elements.
2. `B = { apple, banana, cherry }` → A set of fruits.
3. `C = { x | x is a natural number }` → An infinite set of natural numbers.

### **2. Universal Set (`U`)**

The **universal set** is the set that contains all the elements under discussion. It is usually denoted by `U`.

### **Example**

If we are dealing with natural numbers from 1 to 10, the universal set could be: `U={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`

### **3. Empty Set (`Ø`)**

The **empty set**, or **null set**, is a set that contains no elements. It is denoted by `Ø` or `{}`.

#### **Example**

- The set of even numbers between 1 and 3: `Ø`, because there are no even numbers in that range.
- The set of prime numbers divisible by 4: `Ø`, since no prime number is divisible by 4.

### **4. Subset and Proper Subset**

A set `A` is a **subset** of another set `B` if every element of `A` is also an element of `B`. We write: `A⊆B`

If `A` is a subset of `B` but not equal to `B`, it is called a **proper subset**, written as: `A⊂B`

#### **Example**

If `B = {1, 2, 3, 4, 5}`, then:

- `A = {1, 2, 3}` is a subset of `B → A⊆B`.
- `C = {1, 2, 3, 4, 5}` is not a proper subset of `B` because `C = B`.

### **5. Set Operations**

Set operations help in combining or relating sets in different ways.

#### **(a) Union (`∪`)**

The **union** of two sets `A` and `B` is the set of elements that belong to either `A` or `B` or both. `A∪B={x ∣ x∈A or x∈B}`

##### **Example**

If `A = {1, 2, 3}` and `B = {3, 4, 5}`, then: `A∪B={1,2,3,4,5}`

#### **(b) Intersection (`∩`)**

The **intersection** of two sets `A` and `B` is the set of elements that belong to both `A` and `B`. `A∩B={x ∣ x∈A and x∈B}`

##### **Example**

Using the same sets as above: `A∩B={3}`

#### **(c) Difference (`-` or `\`)**

The **difference** of two sets `A` and `B` is the set of elements that belong to `A` but not to `B`. `A−B={x ∣ x∈A and x ∈/ B}`

##### **Example**

`A−B={1,2}, B−A={4,5}`

#### **(d) Complement (`A^c`)**

The **complement** of a set `A` (denoted as `A^c`) is the set of all elements in the universal set `U` that are not in `A`. `A^c= {x ∣ x∈U and x ∈/ A}`

##### **Example**

If `U = {1, 2, 3, 4, 5}` and `A = {1, 2, 3}`, then: `A^c={4,5}`

#### **(e) Cartesian Product (`A ✕ B`)**

The **Cartesian product** of two sets `A` and `B` is the set of all ordered pairs `(a, b)` where `a in A` and `b in B`. `A×B={(a,b) ∣ a∈A, b∈B}`

##### **Example**

If `A = {1, 2}` and `B = {a, b}`, then: `A×B={(1,a),(1,b),(2,a),(2,b)}`

### **Summary of Set Theory Concepts**

| Concept                             | Definition                                   |
| ----------------------------------- | -------------------------------------------- |
| **Set**                             | Collection of distinct elements              |
| **Universal Set (`U`)**             | Set containing all elements under discussion |
| **Empty Set (`varnothing`)**        | Set with no elements                         |
| **Subset (`subseteq`)**             | A set where all elements are in another set  |
| **Union (`cup`)**                   | Elements in either or both sets              |
| **Intersection (`cap`)**            | Elements common to both sets                 |
| **Difference (`-`)**                | Elements in one set but not the other        |
| **Complement (`A^c`)**              | Elements not in the set (relative to `U`)    |
| **Cartesian Product (`A times B`)** | Set of ordered pairs from two sets           |

> Very hard to make notes in github because of math symbols so let's continue normally.

---
