## Thompson Sampling

Thompson Sampling is a probabilistic algorithm used for decision-making in **multi-armed bandit problems**. It is designed to maximize cumulative rewards by balancing **exploration** (testing less-known options) and **exploitation** (choosing the option with the best-known reward). It achieves this by sampling from probability distributions that represent the uncertainty about each option.

---

## Table of Contents
- [Introduction to Thompson Sampling](#introduction-to-thompson-sampling)
- [Key Concepts](#key-concepts)
- [Steps in Thompson Sampling](#steps-in-thompson-sampling)
- [Advantages](#advantages)
- [Disadvantages](#disadvantages)
- [Applications](#applications)

---

### Introduction to Thompson Sampling

**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/6456840#content)**

Thompson Sampling is a **Bayesian approach** to solving the exploration-exploitation trade-off in multi-armed bandit problems. It uses probability distributions to model the uncertainty about the reward probabilities of different options and makes decisions by sampling from these distributions.

---

### Key Concepts

1. **Beta Distribution**:
   - Used to model the probability of success for each option (e.g., ad, product).
   - The Beta distribution is updated dynamically based on observed rewards.

2. **Prior and Posterior**:
   - **Prior**: Initial belief about the reward probabilities of each option.
   - **Posterior**: Updated belief based on observed outcomes.

3. **Exploration and Exploitation**:
   - **Exploration**: Sampling from distributions to try less-tested options.
   - **Exploitation**: Favoring options with higher probability of success.

---

### Steps in Thompson Sampling

1. **Initialization**:
   - Start with a **prior Beta distribution** $ \text{Beta}(1, 1) $ for each option, representing equal probabilities of success and failure.

2. **Sampling**:
   - For each option $ i $, sample a value $ \theta_i $ from its Beta distribution $ \text{Beta}(\alpha_i, \beta_i) $, where:
     - $ \alpha_i $: Number of successes (rewards) for option $ i $.
     - $ \beta_i $: Number of failures for option $ i $.

3. **Select Option**:
   - Choose the option with the highest sampled value $ \theta_i $.

4. **Observe Reward**:
   - After selecting an option, observe its reward (success or failure).

5. **Update Distribution**:
   - Update the Beta distribution for the chosen option:
     - Increment $ \alpha_i $ for a success.
     - Increment $ \beta_i $ for a failure.

6. **Repeat**:
   - Continue sampling, selecting, observing, and updating over multiple rounds.

---

### Advantages

1. **Efficient Balance**:
   - Balances exploration and exploitation probabilistically.
2. **Scalable**:
   - Performs well in large-scale and real-time applications.
3. **Handles Uncertainty**:
   - Models uncertainty dynamically using Bayesian principles.

---

### Disadvantages

1. **Requires Binary Rewards**:
   - Works best with binary success/failure outcomes.
2. **Complex for Non-Binary Scenarios**:
   - Extending to non-binary rewards (e.g., continuous rewards) is more challenging.
3. **Computational Overhead**:
   - Requires maintaining and updating Beta distributions for all options.

---

### Applications

1. **Online Advertising**:
   - Optimizing ad displays to maximize click-through rates.
2. **Recommendation Systems**:
   - Selecting content to recommend to users.
3. **Clinical Trials**:
   - Allocating resources to test different treatments dynamically.
4. **A/B Testing**:
   - Optimizing experiments by dynamically adjusting allocations.





# Practical Example
See the practical example in the video and the practical notebook **[here](./practical/hierarchical_clustering.ipynb)**.  
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/19875774#content)**