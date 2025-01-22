# Table of Contents
- [Apriori Algorithm](#apriori-algorithm)
  - [Key Concepts](#key-concepts)
  - [Algorithm Steps](#steps-of-the-apriori-algorithm)
## Apriori Algorithm

**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/6455322#content)**

The **Apriori Algorithm** is a popular data mining technique used for **association rule learning**. It identifies frequent itemsets (groups of items that often appear together) in a dataset and derives association rules, which are useful for tasks like market basket analysis.

---

### Key Concepts:
1. **Itemset**:
   - A collection of one or more items.
   - Example: `{bread, butter}` is an itemset.

2. **Support**:
   - The fraction of transactions that contain an itemset.
   - Formula:  
     $$
     \text{Support} = \frac{\text{Transactions containing the itemset}}{\text{Total transactions}}
     $$

3. **Confidence**:
   - Measures the likelihood of item \( B \) being purchased given that \( A \) is purchased.
   - Formula:  
     $$
     \text{Confidence} = \frac{\text{Support of } A \cup B}{\text{Support of } A}
     $$

4. **Lift**:
   - Indicates how much more likely \( B \) is purchased when \( A \) is purchased compared to random chance.
   - Formula:  
     $$
     \text{Lift} = \frac{\text{Confidence of } A \rightarrow B}{\text{Support of } B}
     $$

---

### Steps of the Apriori Algorithm:
1. **Set Minimum Thresholds**:
   - Define the minimum support and confidence levels.

2. **Generate Frequent Itemsets**:
   - Identify itemsets with support greater than or equal to the minimum threshold.

3. **Generate Candidate Itemsets**:
   - Combine frequent itemsets to create larger itemsets (e.g., combine pairs to form triples).

4. **Prune Candidates**:
   - Eliminate itemsets with support below the threshold.

5. **Generate Association Rules**:
   - Use frequent itemsets to generate rules that meet the minimum confidence level.

---

### Example:
Consider a dataset with transactions:
| Transaction | Items                  |
|-------------|------------------------|
| T1          | Bread, Butter          |
| T2          | Bread, Milk            |
| T3          | Bread, Butter, Milk    |
| T4          | Butter, Milk           |

1. **Set thresholds**:  
   Minimum Support = 50%, Minimum Confidence = 70%.

2. **Frequent itemsets**:
   - `{Bread}`: 75% support.
   - `{Butter}`: 75% support.
   - `{Milk}`: 75% support.
   - `{Bread, Butter}`: 50% support.

3. **Generate rules**:
   - Example Rule: `Bread → Butter` with confidence = 66.7%.

---

### Advantages:
- Easy to implement and interpret.
- Effective for small to medium-sized datasets.

---

### Disadvantages:
- Computationally expensive for large datasets.
- May generate a large number of redundant rules.

---

### Applications:
- Market Basket Analysis (e.g., "Customers who buy bread often buy butter").
- Recommendation Systems.
- Fraud Detection.

---

# Practical Example
See the practical example in the video and the practical notebook **[here](./practical/hierarchical_clustering.ipynb)**.  
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/19799914#content)**



### Code Breakdown:

```python
from apyori import apriori
```
- This imports the **`apriori`** function from the **`apyori`** library.
- The **`apriori`** function is used to find frequent itemsets and generate association rules based on user-defined thresholds.

---

```python
rules = apriori(
    transactions=transactions, 
    min_support=0.003, 
    min_confidence=0.2, 
    min_lift=3, 
    min_length=2, 
    max_length=2
)
```
- **`transactions`**:
  - A list of lists where each inner list represents a transaction.
  - Example:
    ```python
    transactions = [
        ['bread', 'butter', 'milk'],
        ['bread', 'milk'],
        ['butter', 'milk'],
        ['bread', 'butter']
    ]
    ```

- **`min_support`**:
  - The minimum support threshold for an itemset to be considered frequent.
  - Example: If `min_support=0.003`, an itemset must appear in at least 0.3% of transactions.

- **`min_confidence`**:
  - The minimum confidence threshold for an association rule.
  - Example: If `min_confidence=0.2`, only rules with at least 20% confidence are considered.

- **`min_lift`**:
  - The minimum lift threshold for an association rule.
  - Example: If `min_lift=3`, only rules with a lift of 3 or higher are included.
  - Lift measures the strength of an association compared to random chance.

- **`min_length`**:
  - The minimum number of items in an itemset.
  - Example: If `min_length=2`, itemsets must contain at least 2 items.

- **`max_length`**:
  - The maximum number of items in an itemset.
  - Example: If `max_length=2`, itemsets can contain at most 2 items.

---
