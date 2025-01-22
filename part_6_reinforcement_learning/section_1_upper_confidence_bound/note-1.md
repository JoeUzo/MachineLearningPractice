


## Upper Confidence Bound (UCB)
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/6456816#content)**

The **Upper Confidence Bound (UCB)** algorithm is a reinforcement learning technique used for **multi-armed bandit problems**. It balances the trade-off between **exploitation** (leveraging known information) and **exploration** (gathering more information about uncertain options) to maximize the cumulative reward over time.

---

### Key Concepts:

1. **Multi-Armed Bandit Problem**:
   - A scenario where you have multiple options (e.g., slot machines or ads to show) with unknown probabilities of rewards.
   - The goal is to find the option with the highest reward while minimizing the cost of exploring less optimal options.

2. **Exploration vs. Exploitation**:
   - **Exploitation**: Choosing the option with the highest known average reward.
   - **Exploration**: Trying out other options to gain more information.

3. **Confidence Bound**:
   - UCB uses a confidence interval to estimate the potential of an option. The upper bound of this interval guides the selection of options.

---

### Formula for UCB:
For each option $ i $ (e.g., a slot machine or ad):

$$
UCB_i = \bar{x}_i + \sqrt{\frac{2 \ln(n)}{n_i}}
$$

Where:
- $ \bar{x}_i $: Average reward of option $ i $ so far.
- $ n $: Total number of trials (total actions taken).
- $ n_i $: Number of times option $ i $ has been chosen.
- $ \sqrt{\frac{2 \ln(n)}{n_i}} $: Exploration term that decreases as $ n_i $ increases, encouraging exploration of less-frequently chosen options.

---

### Steps in the UCB Algorithm:

1. **Initialization**:
   - Start with all options having equal priority.
   - Select each option once to initialize rewards.

2. **Selection**:
   - Compute $ UCB_i $ for each option using the formula.
   - Choose the option with the highest $ UCB_i $.

3. **Reward Update**:
   - Observe the reward from the selected option.
   - Update the average reward ($ \bar{x}_i $) and the number of times the option has been chosen ($ n_i $).

4. **Repeat**:
   - Continue selecting options, updating $ UCB_i $, and refining the rewards.

---

### Example:
Imagine a scenario with 3 slot machines:
- Initially, try each slot machine once.
- Calculate the $ UCB_i $ for all slot machines.
- Select the machine with the highest $ UCB_i $.
- Update the reward and recalculate $ UCB_i $ values.
- Repeat until the best machine is identified.

---

### Advantages:
1. **Efficient Exploration**:
   - Automatically balances exploration and exploitation without manual tuning.
2. **Provable Bounds**:
   - Provides theoretical guarantees for reward maximization in many cases.

---

### Disadvantages:
1. **Assumes Stationarity**:
   - Assumes that the reward probabilities do not change over time.
2. **High Initial Exploration**:
   - May waste resources on suboptimal options initially.

---

### Applications:
1. **Online Advertising**:
   - Selecting ads to display based on click-through rates.
2. **Recommendation Systems**:
   - Suggesting products or content to users.
3. **Clinical Trials**:
   - Allocating resources to test different treatments.


# Practical Example
See the practical example in the video and the practical notebook **[here](./practical/hierarchical_clustering.ipynb)**.  
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/19875724#content)**