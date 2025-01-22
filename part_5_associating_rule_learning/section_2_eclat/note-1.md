## Table of Contents
- [Eclat Algorithm](#eclat-algorithm)
- [Key Concepts](#key-concepts)
- [Steps in the Eclat Algorithm](#steps-in-the-eclat-algorithm)
- [Example](#example)
- [Advantages](#advantages)
- [Disadvantages](#disadvantages)
- [Applications](#applications)
- [Difference Between Eclat and Apriori](#difference-between-eclat-and-apriori)

---


## Eclat Algorithm
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/6455326#content)**

The **Eclat Algorithm** (Equivalence Class Clustering and bottom-up Lattice Traversal) is a popular association rule mining technique that focuses on finding **frequent itemsets** in a dataset. Unlike the Apriori algorithm, which uses a breadth-first search (BFS) and generates candidate itemsets based on horizontal data representation, Eclat adopts a **depth-first search (DFS)** and utilizes a **vertical data representation**.

---

### Key Concepts:

1. **Vertical Data Representation**:
   - Instead of tracking transactions as rows, Eclat maps each item to a list of transaction IDs (TIDs) where it appears.
   - Example:  
     | Item | TID List      |
     |------|---------------|
     | A    | {T1, T3, T4}  |
     | B    | {T2, T3, T5}  |

2. **Intersection for Frequent Itemsets**:
   - Frequent itemsets are found by intersecting the TID lists of individual items.
   - Example:  
     - TID(A) = {T1, T3, T4}  
     - TID(B) = {T2, T3, T5}  
     - TID(A ∩ B) = {T3}.

3. **Support**:
   - Calculated as the size of the intersection of TID lists.
   - Example: Support(A ∩ B) = \(|\text{TID(A ∩ B)}|\).

---

### Steps in the Eclat Algorithm:

1. **Prepare Vertical Representation**:
   - Convert the dataset into a vertical format where each item is associated with its TID list.

2. **Generate Frequent Itemsets**:
   - Start with single-item TID lists.
   - Combine itemsets by intersecting their TID lists to generate larger itemsets.
   - Prune itemsets that do not meet the minimum support threshold.

3. **Repeat Recursively**:
   - Apply the process recursively for each itemset, exploring all possible combinations.

4. **Output Frequent Itemsets**:
   - Collect and output all itemsets that meet the minimum support threshold.

---

### Example:
#### Dataset:
| Transaction | Items       |
|-------------|-------------|
| T1          | A, B, C     |
| T2          | A, C        |
| T3          | B, C, D     |
| T4          | A, D        |
| T5          | B, C        |

#### Vertical Representation:
| Item | TID List      |
|------|---------------|
| A    | {T1, T2, T4}  |
| B    | {T1, T3, T5}  |
| C    | {T1, T2, T3, T5} |
| D    | {T3, T4}      |

- To find frequent itemsets, intersect TID lists:
  - A ∩ B = {T1}.
  - A ∩ C = {T1, T2}.

---

### Advantages:
1. **Efficient for Sparse Data**:
   - Performs well when datasets have many transactions with fewer items per transaction.
2. **No Candidate Generation**:
   - Unlike Apriori, it avoids generating and testing many candidate itemsets.
3. **Simple Implementation**:
   - Based on straightforward intersections of TID lists.

---

### Disadvantages:
1. **Memory Intensive**:
   - Requires storing vertical data representation in memory.
2. **Limited for Dense Data**:
   - Performance can degrade when datasets are dense with many overlapping items.

---

### Applications:
- **Market Basket Analysis**: Finding frequent combinations of products.
- **Web Usage Mining**: Identifying frequently visited pages together.
- **Bioinformatics**: Discovering co-occurring genes or proteins.

---

### Difference Between Eclat and Apriori:
| Feature              | Eclat                     | Apriori                   |
|----------------------|---------------------------|---------------------------|
| Data Representation  | Vertical (TID list)       | Horizontal (transactional)|
| Search Strategy      | Depth-first search (DFS)  | Breadth-first search (BFS)|
| Candidate Generation | No                        | Yes                       |

The Eclat algorithm is a powerful alternative to Apriori when working with datasets that fit its memory and structure requirements. Let me know if you’d like an example implementation!


# Practical Example
See the practical example in the video and the practical notebook **[here](./practical/hierarchical_clustering.ipynb)**.  
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/19806856#content)**