# titanic_dataset-normality-hypothesis-
The one-sample t-test assumes that the data is approximately normally distributed, especially for small sample sizes (like 25). If this assumption is violated, the results of the t-test may not be reliable.


In hypothesis testing, **significance** refers to the threshold at which you decide whether to reject or fail to reject the null hypothesis. This threshold is defined by a **significance level**, denoted by \(\alpha\), which represents the probability of making a **Type I error**—rejecting the null hypothesis when it is actually true.

### Key Concepts of Hypothesis Testing and Significance:

1. **Hypothesis Testing**:
   - **Null Hypothesis (H₀)**: A statement that there is no effect or no difference. It is the hypothesis that the test seeks to reject.
   - **Alternative Hypothesis (H₁)**: A statement that there is an effect or a difference. It represents what you are trying to prove.

2. **Significance Level (\(\alpha\))**:
   - The significance level is the probability of rejecting the null hypothesis when it is true (Type I error). Common significance levels are 0.05 (5%), 0.01 (1%), or 0.10 (10%).
   - For example, a significance level of \(\alpha = 0.05\) means there is a 5% risk of concluding that a difference exists when there is no actual difference.

3. **p-value**:
   - The p-value represents the probability of observing the data, or something more extreme, given that the null hypothesis is true.
   - If the **p-value** is **less than or equal to** the chosen significance level (\(\alpha\)), you **reject the null hypothesis**. This means there is sufficient evidence to support the alternative hypothesis.
   - If the **p-value** is **greater than** the significance level, you **fail to reject the null hypothesis**. This means there is not enough evidence to support the alternative hypothesis.

4. **Interpreting the Significance in Hypothesis Testing**:
   - **Reject H₀**: If the p-value is less than \(\alpha\), the result is statistically significant, indicating evidence against the null hypothesis in favor of the alternative hypothesis.
   - **Fail to Reject H₀**: If the p-value is greater than \(\alpha\), the result is not statistically significant, indicating insufficient evidence to reject the null hypothesis.

### Significance in Your Context:

When conducting hypothesis tests like the **one-sample t-test**, the **significance** level determines whether the difference between the sample mean and the population mean is statistically significant or could have occurred by random chance.

For example, suppose you conducted a one-sample t-test with the following:

- **Null Hypothesis (H₀)**: The sample mean is equal to the population mean (\(\mu = \mu_0\)).
- **Alternative Hypothesis (H₁)**: The sample mean is different from the population mean (\(\mu \neq \mu_0\)).

If you choose a significance level of 0.05 and the resulting p-value is 0.03:

- Since **0.03 < 0.05**, you would **reject the null hypothesis** and conclude that there is a statistically significant difference between the sample mean and the population mean.
- Conversely, if the p-value were 0.08, since **0.08 > 0.05**, you would **fail to reject the null hypothesis**, indicating that the observed difference is not statistically significant and could be due to random chance.

### Summary:

- **Significance** in hypothesis testing determines whether to reject or fail to reject the null hypothesis based on a predetermined significance level (\(\alpha\)).
- The **p-value** is compared against \(\alpha\) to make this decision.
- If the p-value is **less than \(\alpha\)**, the result is **statistically significant**, and you reject the null hypothesis.
- If the p-value is **greater than \(\alpha\)**, the result is **not statistically significant**, and you fail to reject the null hypothesis.

---------------------------------------------------------------------------------------------------------------------------------------------------------------


A **one-sample t-test** is a statistical test used to determine whether the mean of a single sample is significantly different from a known or hypothesized population mean. This test is useful when you want to compare the average of a sample to a known value to see if they differ significantly.

### Key Concepts of One-Sample t-Test:

1. **Purpose**:
   - To test if the mean of a single sample is significantly different from a known or specified population mean (null hypothesis).

2. **Hypotheses**:
   - **Null Hypothesis (H₀)**: The sample mean is equal to the population mean.
     \[
     H_0: \mu = \mu_0
     \]
   - **Alternative Hypothesis (H₁)**: The sample mean is not equal to the population mean.
     \[
     H_1: \mu \neq \mu_0
     \]

3. **Formula for the t-Statistic**:
   The formula for calculating the t-statistic in a one-sample t-test is:

   \[
   t = \frac{\bar{x} - \mu_0}{\frac{s}{\sqrt{n}}}
   \]

   where:
   - \(\bar{x}\) = Sample mean
   - \(\mu_0\) = Population mean (the value you are comparing against)
   - \(s\) = Sample standard deviation
   - \(n\) = Sample size

4. **Assumptions**:
   - The data is approximately normally distributed (especially important for small sample sizes).
   - The sample data is independent and randomly selected.
   - The data should be measured on a continuous scale (interval or ratio).

5. **Interpretation of Results**:
   - **t-statistic**: Measures how far the sample mean is from the population mean in terms of standard error. The larger the absolute value of the t-statistic, the more evidence against the null hypothesis.
   - **p-value**: Represents the probability of obtaining a test statistic as extreme as the one observed if the null hypothesis is true. If the p-value is less than a chosen significance level (e.g., 0.05), the null hypothesis is rejected in favor of the alternative hypothesis.

6. **Types of t-Tests**:
   - **Two-tailed test**: Tests if the sample mean is significantly different from the population mean (it could be either higher or lower).
   - **One-tailed test**: Tests if the sample mean is either significantly higher or lower than the population mean (but not both).

### Example:

Suppose a school claims that the average score of its students on a math test is 70. You collect a sample of 30 students and find that their average score is 65 with a standard deviation of 10. You want to test if the average score of the sample is significantly different from 70.

#### Step-by-step Solution:

1. **Set Hypotheses**:
   - \(H_0: \mu = 70\)
   - \(H_1: \mu \neq 70\)

2. **Compute the t-statistic**:
   \[
   t = \frac{65 - 70}{\frac{10}{\sqrt{30}}} = \frac{-5}{1.825} \approx -2.74
   \]

3. **Find the p-value**: Use a t-distribution table or statistical software. With 29 degrees of freedom (df = n - 1 = 30 - 1), you can look up the p-value.

4. **Decision**:
   - If the p-value < 0.05 (assuming a significance level of 0.05), reject the null hypothesis. Otherwise, do not reject it.

### Performing One-Sample t-Test in Python:

You can use `scipy.stats` to perform a one-sample t-test in Python:

```python
import numpy as np
from scipy import stats

# Sample data
sample = np.array([65, 70, 62, 68, 74, 60, 66, 72, 75, 64, 67, 69, 71, 63, 68, 70, 65, 72, 73, 61, 66, 64, 67, 71, 69, 70, 66, 68, 63, 74])

# Population mean
pop_mean = 70

# Perform one-sample t-test
t_statistic, p_value = stats.ttest_1samp(sample, pop_mean)

print("t_statistic:", t_statistic)
print("p_value:", p_value)
```

This will compute the t-statistic and p-value for your data to determine if there is a significant difference between the sample mean and the hypothesized population mean.
