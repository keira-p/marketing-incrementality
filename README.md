## Estimating Marketing Incrementality Under Selection Bias

This project explores a common problem in marketing analytics:

*Did a campaign actually drive incremental conversions, or just capture users who were already likely to convert?*

Using a simulated dataset with built-in selection bias, I compare different approaches to estimating campaign impact, and show how easily naive methods can mislead.

### 🔍 Key Result

```
Naive Lift: 1.98%
PSM Lift:   5.29%
A/B Lift:   1.10%
True Lift:  1.00%
```

- A simple comparison suggests the campaign increased conversion by ~2 percentage points.
- However, the true incremental impact is closer to ~1ppt.
- Attempts to correct for bias using propensity score matching produced an even larger estimate (~5.3ppt), highlighting how sensitive observational methods can be.
- A randomised A/B test, by contrast, recovered the true effect (~1.1ppt)

#### 🧠 What This Shows

- **Correlation ≠ causation** — Higher conversion among exposed users does not imply incremental impact
- **Selection bias matters** — Higher-intent users are more likely to be targeted
- **Observational methods are fragile** — Results depend heavily on modelling and assumptions
- **A/B testing is the most reliable approach** — Randomisation provides a clean estimate of incrementality

### ⚙️ Approach

Simulated user-level dataset with:

- Baseline purchase propensity
- Biased treatment assignment (higher-intent users more likely to see ads)

Estimated lift using:

- Naive comparison
- Propensity score matching (PSM)
- Randomised A/B test

Compared all estimates against the known ground truth

### 📊 Example Output

The chart below compares estimated lift across methods vs the true effect:

![Lift comparison chart](/images/lift_comparison.png)

*Naive and PSM estimates overstate true lift, while A/B aligns with the ground truth.*

### 💬 Practical Takeaway

- Naive attribution can significantly overstate campaign performance.

- Even when attempting to correct for bias using observational methods, results can be unstable or misleading.

- For any meaningful investment decision, a controlled holdout or A/B test is the most reliable way to measure true incremental value.

### 📂 Files
incrementality_simulation_and_causal_estimation.ipynb — full analysis
