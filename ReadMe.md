## Levels of Measurement
### Nominal
- Predetermined Categories.
- Can't be sorted
Examples: 
	- Animal Classification
	- Political Party
### Ordinal
- Can be sorted.
- Lacks Scale
Example:
	- Survery Responses.
### Interval
- Provides Scale
- Lacks a "zero" point
Example:
	Temperature (Can be negative)
### Ratio
- Values have a true zero point
Examples:
	Age, Weight, Salary.
### Population vs Sample
- Population = All members of a group.
- Sample: Subset of population.

## Measurement of Central Tendency
- Mean: Average
- Median: Middle Value
- Mode: Most Occuring Value"# statistics-and-probabililty-for-machine-learning" 

## Measurement of Dispersion
- Range: Max - Min
- Variance: Sum of square distances from each point to the mean.
  - Sample Variance: s^2 = Σ(xi - ¯x)^2 / (n - 1) (This is called Bessel's correction)
  - Population Variance: σ^2 = Σ(xi - μ)^2 / N
  - Bessel's correction is an approach to reduce the bias due to some sort of finite sample size.
- Standard Deviation:
  - Square root of the variance
  - Benefit: Same unit as the sample
  - Meaningful to talk about: Values that lie within one standard deviation of the mean.

## Qurtile and IQR:
- Consider a series.
- Divide the series.
- Divide the subseries.

- Boxplot can be used to show quartile range.
- IQR: Q2 and Q3
### Fences and Outliers
- Fence: 1.5 times the width of the IQR.
- Anything outside the fence is an outlier.
- This is determined by data, not an arbitrary percentage!
- Max = Max of IQR + 1.5*Max of IQR
- Min = Min of IQR - 1.5*Min of IQR
- Everything outside Max and Min is considered as outlier.
- When drawing box plots, the whiskers are brought inward to the outmost values inside the fence.

## Bivariate Data And Covariance.
- Compare two variables.
- By convention, the x-axis is set to the independent variable.
- Y-axis is set to the dependent variable, or that which is being measured relative to x.
## Bivariate Data
- Scatter plots may uncover a correlation between two variables.
- They can't show causality!
- Correlation between two variables does not prove causality.
- More statistical analysis is needed to determine causality!
## Covariance
- Common way to compare two variables is to compare their variances- How far from each item's mean do typical values fall?
- First challenge is to match scale.
- Comparing height in inches to weight in pounts isn't menaingful unless we develop a standard score to normalize the data.
- Population Covariance: σ_xy = Σ((xi - μ_x) * (yi - μ_y)) / N

## Pearson Correlation Coefficient
- In order to normalize values coming from two different distributions, we use:
- r = Σ((xi - ¯x) * (yi - ¯y)) / sqrt(Σ(xi - ¯x)^2 * Σ(yi - ¯y)^2)
- Values fall between +1 and -1, where 
  - 1 = Total Positive Linear Correlation.
  - 0 = No Linear Correlation.
  - -1= Total Negative linear Correlation.



# Probability
- Value betwee 0 and 1 that a certain event will occur.
- Trials have no memory.
## Permutations.
- Set of objects is an arrangement of the objects in a certain order.
- For n: n!
- For subset: n!/(n-r)!
- Allowing repeatations: n^n
## Combinations.
- Order does not matter.
- n!/((n-r)!*r!)
- Combinations with repeatations
- (n+r-1)!/(r!*(n-1)!)

# Distribution
- A distribution describes all of the probable outcomes of a variable.
- In a discrete distribution, the sum of all the individual probabilities must equal 1.
- In a continuous distribution, the area under the probability curve equals 1.
### Discrete probability distributions
- Also called as probability mass functions.
  - Uniform Distribution.
  - Binomial Distribution.
  - Poisson Distribution.
### Uniform Distribution
- Rolling a fair die has 6 discrete equally probable outcomes.
- Probabilities are evenly distributed.

### Binomial Distribution
- Binomial means there are two discrete mutually exclusive outcomes of trial.
  - Heads/Tails, On/Off, Sick/Healthy.
### Bernoulli Trial
- Is a random experiment in which there are only two possible outcomes.
  - Success/Failure
- A Series of trials n will follow a binary distribution so long as 
  - a.> The probability of success p is constant.
  - b.> Trials are independent of one another.
### Binomial Probability Mass Function.
- Given the probability of observing x successes in n trials.
- The probability of success on a single trial is denoted by p.
- Assumes that p is fixed for all trials.
- P(X = k) = (n Combination k) * p^k * (1 - p)^(n - k)
Example
- If you roll a die 16 times what is the probability that a five comes up 3 times?
- Excel BINOM.DIST(3,16,1/6,FALSE) 
- from scipy.stats import binom
- binom.pmf(3,6,1/6)

## Poisson Distribution
- A binomial distribution considers the number of successes of n trials.
- A Poisson Distribution considers the number of successes (per unit of time/distance)* over the course of many.
- Calculation of the Poisson PMF starts with a mean expected value.

\[ P(X = k) = \frac{e^{-\lambda} \cdot \lambda^k}{k!} \]

Where:
- \( P(X = k) \) is the probability of observing \( k \) events in the given interval,
- \( e \) is the base of the natural logarithm (approximately 2.71828),
- \( \lambda \) (lambda) is the average rate (mean) of events occurring in the given interval,
- \( k \) is the number of events that occurred,
- \( k! \) is the factorial of \( k \), i.e., the product of all positive integers up to \( k \).

## Continuous Distributios(Probability Density Functions).

### Normal Distribution.
- Height, Weight, Blood Pressure, Test Scores, Measuremet Errors.
- These data sources tend to be around a central value with no bias left or right, and it gets close to a "Normal Distribution".
- Area under the curve = 1.
- Also called as Bell Curve or Gaussian Distribution.
- Always Symmetrical.
  - Assymetrical curves display skew and are not normal.
  - Right Shifted(Negative skew); left Shifted(Positive skew).
- Probability of a specific outcome is zero.
- We can only find probabilities over a specified interval or range of outcomes.
- Lower Tail ->Mean, Median, Mode <-Upper Tail.
- Mean = 0, Standard Deviation = 0.
- 68.27 % Of all values fall in 1σ.
- 95.45 % Of all values fall in 2σ.
- 99.73 % Of all values fall in 3σ.
- All normal curves exhibit the same behavior.
- Symmetry about the mean.
- However the mean does not have to be zero and σ does not have to be 1.
- Other populations can be normal as well.

## Normal Distribution and Z Scores.

\[ f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}} \]

Where:
- \( f(x) \) is the probability density function,
- \( \mu \) (mu) is the mean,
- \( \sigma \) (sigma) is the standard deviation.


- Real-life datasets often follow a normal distribution, making it essential to understand standardization for statistical analysis.
- Z-scores allow converting values to a standard normal distribution, facilitating percentile calculations.
- The normal distribution follows a complex formula involving mean (μ), standard deviation (σ), and mathematical constants like Euler's number and Pi.
- Z-Score = (X-Mean)/σ
- Z-scores standardize data points by measuring deviations from the mean in terms of standard deviations.
- Z-tables map Z-scores to areas under the standard normal distribution curve, aiding in percentile determination.
- While manual calculation using Z-tables is illustrated, software tools like Excel or Python are commonly used for efficiency.
- An example demonstrates Z-score application in assessing job applicants' standardized test scores, aiding decision-making.
- Understanding Z-scores is fundamental for statistical analysis, to be explored further in the subsequent statistics section.
### Z-Scores in MS Excel
- =NORMSDIST(B2)
- =NORMSINV(B3)
### Python
- from scipy imports stats
- z=.70
- stats.norm.cdf(z)
- p=.95
- stats.norm.ppf(p)



# Statistics
- Parameter: Is a characteristics of a population. Often we want to understad the parameters.
- Statistic: Is a characteristic of a sample. Often we apply statistical inferences to the sample in an attempt to describe the population.
- Variable: Characteristic that describe a member of the sample.
  - Discrete/Continuous.

## Sampling Techniques.
- One of the great benefits of statistical models is that a reasonably sized (>30) random sample will almost always reflect the population.
- How do we select members ramdomly, and avoid bias?
### Sampling Bias
- There are several forms of bias:
- Selection Bias: Most common, this type of bias favors those members of a population who are more inclined and able to answer polls.
  - Undercoverage Bias: Making too few observations or omitting entire segments of a population. Examples: Survey of hospital employees during day time.(neglects night shift)
  - Self-Selection Bias: People who voluteer may differ significantly from those in the population who don't.(Online survey of team)
  - Healthy-User Bias: The sample may come from a healthier segment of the overall population.
  - Survivorship Bias: If a population improves over time, it may be due to lesser members leaving the population due to death, expulsion, relocation, etc. Example: Planes coming back from war.
### Types of Sampling
- Random
  - Every member of a population has an equal chance of being selected.
  - However, since samples are usually much smaller than populations, there's a chance that entire demographics might be missed.
- Stratified Random
  - Groups within a population are adequately represented.
  - First, divide the population into segments based on some characteristic.
  - Members cannot belong to two groups as once.

## Central Limit Theorem
- What makes sampling such a good statistical tool is the Central Limit Therorem.

## Standard Error
### Standard Error Of The Mean
- Where the population standard deviation describes how wide individual values stray from the population mean, The standard error of the mean describes how far a sample mean may stray from the population mean.
- If the population standard deviation is known then sample standard error of the mean can be Calculated as.:
  - SE-sample = sigma / sqrt(n)

## Hypothesis Testing:
- Application of the statistical methods to real-world questions.
- We start with assumption, called the null hypothesis.
- We run experiment to test this null hypothesis.
- Based on the results of the experiment we either reject or fail to reject the null hypothesis.
- If the null hypothesis is rejected, then we say the data supports another, mutually exclusive alternate hypothesis.
- We never "Prove" A Hypothesis.

### Framing the Hypothesis
- How do we frame the question that forms our null hypothesis?
- At the start of the experiment, the null hypothesis is assumed to be true.
- If the data fails to support the null hypothesis, only then can we look to an alternative hypothesis.
- If testing something assumed to be true the null hypothesis can reflect the assumption:
- Alternate Hypothesis: Opposite of Null Hypothesis.
- The null hypothesis should contain equality(=,<=,>=).
- Alternate Hypothesis should not have an equality (!=,<,>)

### Hypothesis Testing.
- We run an experiment and record the result.
- Assuming our null hypothesis is valid, if the probability of observing these results is very small (inside 0.05) then we reject the null hypothesis.
- Here 0.05 is our level of significance.
- The level of significance α is the area inside the tail(s) of our null hypothesis.
- If α = 0.05 and the alternative hypothesis is less than null, then the left-tail of our probability curve has an area of 0.05.
- The level of significace α is the area inside the tail(s) of our null hypothesis.
- If α = 0.05 and the alternative hypothesis is more than nullm then the right tail of our probability curve has an area of 0.05.
If α = 0.05 and the alternative hypothesis is not equal to null then the two tails of our probability curve share an area of 0.05.
- ### Exponential Distribution.

# Regression
## Linear Regression
- Goal of regression is to develop an equation or formula that best describes the relationship between variables.

# Chi-Square Analysis.
### In 1900 Karl Pearson wrote a paper.
- On the criterion that a given system of deviations from the probable in the case of a Correlated System of Variables is such that it can be reasonably supposed to have arisen from Random Sampling.
- In short "Goodness of fit"
- Chi-Squared Test is used to determine the probability of an observed frequency of events given an expected frequency.
- Chi-Square formula considers the sum of square distances between observed values O and expected values E, divided by each expected value.
- Chi-Square Test for Independence (Contingency Table):
- χ² = Σ[(O_{ij} - E_{ij})² / E_{ij}]
- Chi-Square Goodness of Fit Test:
- χ² = Σ[(O_i - E_i)² / E_i]
- A low χ² value means a high correlation between the observed values and expected values.
