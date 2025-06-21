# PST

Status: Done

Způsoby popisu rozdělení náhodných veličin a vektorů. Odhady parametrů rozdělení.
Základní statistické testy. Markovské řetězce a jejich asymptotické vlastnosti. 

• Definice pravděpodobnosti (Kolmogorovova), nezávislost náhodných jevů, podmı́něná pravděpodobnost, Bayesova věta. Pojem náhodné veličiny, popis jejı́ho rozdělenı́ pomocı́ distribučnı́ funkce, hustoty, pravděpodobnostnı́ funkce. Střednı́ hodnota, rozptyl, směrodatná
odchylka, momenty náhodných veličin. Základnı́ typy spojitých a diskrétnı́ch rozdělenı́.

• Náhodné vektory a jejich popis. Nezávislost náhodných veličin, kovariance a korelace.

• Čebyševova nerovnost, centrálnı́ limitnı́ věta.

• Základnı́ pojmy statistiky, náhodný výběr, empirické rozdělenı́.

• Obecné vlastnosti odhadů parametrů. Odhady střednı́ hodnoty, rozptylu, směrodatné odchylky, momentů. Odhady parametrů metodou momentů a metodou maximálnı́ věrohodnosti. Intervalové odhady.

• Princip statistického testovánı́ hypotéz. Testy střednı́ hodnoty a rozptylu, porovnánı́ dvou
rozdělenı́, χ2 -test dobré shody, test nezávislosti v kontingenčnı́ tabulce.

• Markovovy řetězce: základnı́ pojmy a vlastnosti, popis přechodovým diagramem a maticı́
přechodu. Klasifikace stavů, periodicita, rozložitelnost. Asymptotické chovánı́ Markovových
řetězců.

## Probability axioms

### Sigma algebra

System of all subsets of a set such that 

![image.png](assets/image.png)

If the original set is a set of random elementary events, then every element of the sigma algebra is also an event (e.g. an union of elementary events)

### Kolmogorov probability

![image.png](assets/image%201.png)

This defines a probability space

![image.png](assets/image%202.png)

Some key properties

![image.png](assets/image%203.png)

### Conditional probability

![image.png](assets/image%204.png)

![image.png](assets/image%205.png)

We have a very important chain rule

![image.png](assets/image%206.png)

The law of total probability allows us to compute probabilities from disjoint subsets and their respective conditionals

![image.png](assets/image%207.png)

### Bayes theorem

![image.png](assets/image%208.png)

Law of total probability + conditional probability

### Independence

![image.png](assets/image%209.png)

Alternative definition uses conditional probability and says P(A) = P(A|B) iff A independent of B (reduces to the product rule I guess)

Total independence >> pairwise independence

## Random Variables

![image.png](assets/image%2010.png)

“a random number”

![image.png](assets/image%2011.png)

### Distribution Function

![image.png](assets/image%2012.png)

Probability mass/cumulative distribution function tells us the probability for any random variable how likely it is to fall under some threshold

![image.png](assets/image%2013.png)

### Discrete RV

![image.png](assets/image%2014.png)

There exists a sequence (a mapping $\mathbb{N} \to \mathbb{R}$) of values of the RV and the respective probability of each value (nonzero - gaps in integers).

CDF is computed as the sum of discrete values

![image.png](assets/image%2015.png)

### Continuous RV

![image.png](assets/image%2016.png)

The CDF is an integral in this case

![image.png](assets/image%2017.png)

### Mixed RV

A random variable can be expressed as a mixture (a convex combination) of continuous and discrete random variables

![image.png](assets/image%2018.png)

We can mix continuous and discrete however we like in a fully general fashion. Don’t forget the proper limits to handle both continuous and discrete points.

### Quantile function

![image.png](assets/image%2019.png)

“inverse” of the CDF. Maps probability of X ≤ x to x

### Expected Value

![image.png](assets/image%2020.png)

The exact calculation depends on the type of the random variable

![image.png](assets/image%2021.png)

It is completely linear (superposition holds).

We can transform the random variable using an arbitrary function and compute the expectation ($\phi(x)$ is also a random variable)

![image.png](assets/image%2022.png)

### Higher-order moments

![image.png](assets/image%2023.png)

Don’t forget to use the shortcut $\mathbb{V}[X] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$  

## Concentration inequalities

### Chebyshev

![image.png](assets/image%2024.png)

## Instances of distributions

### Bernoulli

Coin flip distribution

![image.png](assets/image%2025.png)

### Binomial

Sum of repeated Bernoulli flips

![image.png](assets/image%2026.png)

### Poisson Distribution

Probability of a number of events happening on some constrained space (time, spatial). E.g. number of broken bulbs in 5 hours in my room. 

![image.png](assets/image%2027.png)

![image.png](assets/image%2028.png)

### Geometric Distribution

Number of failed attempts before the first successful one (order-sensitive)

![image.png](assets/image%2029.png)

### Uniform

Useful probably only when we know something is bounded and cannot make any other prior assumptions about it.

![image.png](assets/image%2030.png)

### Exponential

Time until the event occurs (e.g. customer walks into a store)

![image.png](assets/image%2031.png)

![image.png](assets/image%2032.png)

### Normal Distribution

“Everything is normally distributed” - me

![image.png](assets/image%2033.png)

Some nice properties

![image.png](assets/image%2034.png)

Invariance to linear transforms is a big one.

## Convolution

![image.png](assets/image%2035.png)

![image.png](assets/image%2036.png)

![image.png](assets/image%2037.png)

![image.png](assets/image%2038.png)

## Random Vectors

![image.png](assets/image%2039.png)

A randomly-sampled point in $\mathbb{R}^n$

### Distribution Function

![image.png](assets/image%2040.png)

The properties as we know them but coordinate-wise

### Discrete vs Continuous

![image.png](assets/image%2041.png)

The distribution function is calculated coordinate-wise like in single variable case

![image.png](assets/image%2042.png)

Continuous case is again the same

![image.png](assets/image%2043.png)

### Marginal distribution

In the case of random vectors, we may want to isolate the probabilities in one or a few coordinates. We can integrate/sum over the rest.

![image.png](assets/image%2044.png)

![image.png](assets/image%2045.png)

### Properties

![image.png](assets/image%2046.png)

### Independence of a set of random vars

Same as random events, just multiply probs

![image.png](assets/image%2047.png)

How to test?

![image.png](assets/image%2048.png)

### Covariance of independent RVs

![image.png](assets/image%2049.png)

## Central Limit Theorem

![image.png](assets/image%2050.png)

![image.png](assets/image%2051.png)

## Statistics

![image.png](assets/image%2052.png)

### Quantiles

![image.png](assets/image%2053.png)

![image.png](assets/image%2054.png)

### Empirical Distribution Function

![image.png](assets/image%2055.png)

## Parameter estimation

Point estimates

![image.png](assets/image%2056.png)

### Bias, Asymptotic Efficiency

![image.png](assets/image%2057.png)

### Moment matching

![image.png](assets/image%2058.png)

### MLE

![image.png](assets/image%2059.png)

Discrete: use the probability function

Continuous: use the density

### Confidence Interval

![image.png](assets/image%2060.png)

Example application for a Normal Distribution with known Variance

![image.png](assets/image%2061.png)

With unknown variance used the student’s t-distribution

![image.png](assets/image%2062.png)

Using these alternative distributions

![image.png](assets/image%2063.png)

We can estimate the expected value of an arbitrary distribution using CLT

![image.png](assets/image%2064.png)

Prove by constructing the CLT estimate of the sample mean and use the fact that $\frac{S_n}{n} \to 1$ as $n \to \infty$. Special modification for Bernoulli and Poisson: estimate the sigma parameter directly from MLE. 

## Hypothesis Testing

![image.png](assets/image%2065.png)

![image.png](assets/image%2066.png)

### Mean of Normal Distribution

![image.png](assets/image%2067.png)

Idea: the test statistic corresponds to an empirically-estimated random variable where we use the parameters of the sample mean distribution. The resulting RV is distributed according to the student t-distribution with n-1 DoF. Then simply test if the absolute value falls within the defined confidence interval.

TODO: ask michal why absolute value

Pairwise variant to test differences in mean values

![image.png](assets/image%2068.png)

Before performing the first one, we should test whether the variances agree

![image.png](assets/image%2069.png)

Using the fisher distribution

![image.png](assets/image%2070.png)

### Pearson Chi-square

Given a multinomial distribution

![image.png](assets/image%2071.png)

Fake the normally-distributed RVs, note the variance is computed differently because the components of the sample are not independent. Once we obtain the chi-square variable, simply test its quantile.

![image.png](assets/image%2072.png)

### Contingency Table Independence

![image.png](assets/image%2073.png)

We are testing the independence of two discrete random variables with arbitrary finite ranges. Construct a table with counts for each one of the value combinations. Then compute marginals for each row and column. Finally, compute the discrepancy between expected frequency (obtained as a product of the marginal) and the recorder one, in a “fake-normal-distribution” fashion. This is chi-square distributed, then evaluate against the quantile.

Note: the term $\frac{n_{i.}n_{.j}}{n}$ comes from the following observation:

for independent events $P(A \cap B) = P(A)P(B)$

obtain the frequencies after n samples as $nP(A \cap B) = nP(A)P(B)$. However, the marginals correspond to $nP(A)$ and $nP(B)$ respectively, therefore use this:  $nP(A \cap B) = \frac{nP(A)nP(B)}{n}$

## Markov Chain

![image.png](assets/image%2074.png)

First-order Markov chain depends only on the previous state.

### Transition probabilities

![image.png](assets/image%2075.png)

![image.png](assets/image%2076.png)

Putting the probabilities into a matrix, we get the probability transition matrix, which is stochastic!

![image.png](assets/image%2077.png)

This is for a homogeneous chain!

The matrix is row-stochastic (rows sum up to 1).

![image.png](assets/image%2078.png)

We can compute the power of this matrix to get a simple result

![image.png](assets/image%2079.png)

![image.png](assets/image%2080.png)

### State classification

![image.png](assets/image%2081.png)

![image.png](assets/image%2082.png)

![image.png](assets/image%2083.png)

Periodic state = all return times are multiple of d

![image.png](assets/image%2084.png)

This is basically the same as graph connectivity, except the edges are stochastic.

![image.png](assets/image%2085.png)

Cannot be decomposed → just one closed component

If we arrive at an absorbing state, we can never leave

If we ever arrive at an absorbing state, we will always get stuck → the chain gets stuck

### Stationary Distribution

![image.png](assets/image%2086.png)

Lambda 1 eigenvector of the transition matrix.

Exists in a nondecomposable markov chain with finite number of states

For a decomposable chain, we can find it as follows:

![image.png](assets/image%2087.png)

### Limit of a Markov Chain with Absorbing states

![image.png](assets/image%2088.png)

Analogy of a geometric series

We can also find the stationary distribution using the “infinite recursion” series of equations.