### Steps in the Upper Confidence Bound Algorithm:

**Step 1**: At each round $ n $, for each option $ i $ (e.g., ad):
- $ N_i(n) $: The number of times option $ i $ has been selected up to round $ n $.
- $ R_i(n) $: The total reward received from option $ i $ up to round $ n $.

---

**Step 2**: Use the above numbers to compute:
1. **The average reward** of option $ i $ up to round $ n $:  
   $$
   \bar{r}_i(n) = \frac{R_i(n)}{N_i(n)}
   $$
2. **The confidence interval** for option $ i $ at round $ n $:  
   $$
   \Delta_i(n) = \sqrt{\frac{3 \log(n)}{2 N_i(n)}}
   $$
   The confidence interval is represented as:  
   $$
   \left[\bar{r}_i(n) - \Delta_i(n), \bar{r}_i(n) + \Delta_i(n)\right]
   $$

---

**Step 3**: At each round, select the option $ i $ that maximizes the **Upper Confidence Bound**:
$$
UCB_i(n) = \bar{r}_i(n) + \Delta_i(n)
$$

This ensures a balance between exploration (trying less frequently selected options) and exploitation (selecting the option with the highest known reward).
