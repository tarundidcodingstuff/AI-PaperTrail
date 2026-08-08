# Harvard Stat 110 — Quant Trading Study Notes

These notes are designed as a **learn + practice** guide for probability preparation for quantitative-trading interviews.

The goal is not to memorize formulas blindly. For every concept:

1. Understand what it means.
2. Know the formula.
3. Solve a simple example.
4. Solve a mixed problem without being told the topic.
5. Explain the reasoning aloud.

---

## 1. Sample Spaces and Events

A sample space `Ω` contains all possible outcomes.

An event is a subset of the sample space.

For a die:

`Ω = {1,2,3,4,5,6}`

If `A = {2,4,6}`, then:

`P(A) = 3/6 = 1/2`

Operations:

- Complement: `Aᶜ`
- Union: `A ∪ B` = A or B
- Intersection: `A ∩ B` = A and B

Rules:

`P(Aᶜ) = 1 - P(A)`

`P(A ∪ B) = P(A) + P(B) - P(A ∩ B)`

### Example

Roll a die. What is the probability of an even number OR a number greater than 4?

A = {2,4,6}, B = {5,6}

`A ∩ B = {6}`

So:

`P(A ∪ B) = 3/6 + 2/6 - 1/6 = 2/3`

---

# 2. Counting

## Multiplication Rule

If step 1 has `a` choices and step 2 has `b` choices:

`N = ab`

Example: 3 shirts and 4 pants give:

`3 × 4 = 12`

outfits.

## Factorial

`n! = n(n-1)...1`

Examples:

`5! = 120`

`0! = 1`

## Permutations

Use when **order matters**:

`P(n,k) = n!/(n-k)!`

Example: Choose president, vice president and secretary from 10 people:

`10 × 9 × 8 = 720`

## Combinations

Use when **order does not matter**:

`C(n,k) = n!/[k!(n-k)!]`

Example:

`C(10,3) = 120`

Memory trick:

- Permutation = positions
- Combination = collection

## Stars and Bars

Nonnegative solutions of:

`x₁ + ... + xₖ = n`

are:

`C(n+k-1,k-1)`

Positive solutions:

`C(n-1,k-1)`

Example: 5 identical balls into 3 boxes, empty boxes allowed:

`C(7,2) = 21`

---

# 3. Inclusion–Exclusion

Two events:

`P(A ∪ B) = P(A)+P(B)-P(A∩B)`

Three events:

`P(A∪B∪C)`

`= P(A)+P(B)+P(C)`
`- P(A∩B)-P(A∩C)-P(B∩C)`
`+ P(A∩B∩C)`

Memory:

**Add singles → subtract pairs → add triples → ...**

---

# 4. Conditional Probability

Fundamental formula:

`P(A|B) = P(A∩B)/P(B)`

Read it as:

> Probability of A given B.

Therefore:

`P(A∩B) = P(A|B)P(B)`

and:

`P(A∩B) = P(B|A)P(A)`

### Example

If a card is known to be a face card, what is the probability it is an Ace?

There are no Aces among J/Q/K:

`P(Ace | Face) = 0`

---

# 5. Bayes' Theorem

`P(A|B) = P(B|A)P(A)/P(B)`

For multiple hypotheses:

`P(Aᵢ|B) = P(B|Aᵢ)P(Aᵢ) / Σⱼ P(B|Aⱼ)P(Aⱼ)`

Think:

> Bayes reverses the conditioning.

### Example

Disease prevalence = 1%.

Sensitivity = 95%.

False-positive rate = 5%.

`P(D)=0.01`

`P(+|D)=0.95`

`P(+|Dᶜ)=0.05`

First calculate:

`P(+) = 0.95(0.01) + 0.05(0.99) = 0.059`

Then:

`P(D|+) = 0.95(0.01)/0.059 ≈ 0.161`

So a positive test gives about a 16.1% probability of disease.

---

# 6. Law of Total Probability

If `A₁,...,Aₙ` partition the sample space:

`P(B) = Σᵢ P(B|Aᵢ)P(Aᵢ)`

Example:

Factory A makes 60% of products and has a 2% defect rate.

Factory B makes 40% and has a 5% defect rate.

`P(D) = 0.6(0.02)+0.4(0.05)=0.032`

So the defect probability is 3.2%.

---

# 7. Independence

A and B are independent if:

`P(A∩B)=P(A)P(B)`

Equivalent, when `P(B)>0`:

`P(A|B)=P(A)`

Important:

**Mutually exclusive does not mean independent.**

If positive-probability events are mutually exclusive, their intersection is 0, so they cannot also satisfy `P(A∩B)=P(A)P(B)`.

---

# 8. Conditional Independence

A and B are conditionally independent given C if:

`P(A∩B|C)=P(A|C)P(B|C)`

This is the assumption behind Naive Bayes.

---

# 9. Random Variables

A random variable maps outcomes to numbers.

Example: for a die, `X ∈ {1,...,6}`.

## PMF

For discrete X:

`pX(x)=P(X=x)`

with:

`pX(x) ≥ 0`

and:

`Σ pX(x)=1`

## CDF

`FX(x)=P(X≤x)`

---

# 10. Continuous Random Variables

For continuous X:

`P(a<X<b)=∫[a,b] fX(x) dx`

and:

`FX(x)=∫[-∞,x] fX(t)dt`

Important:

`P(X=x)=0`

for a continuous random variable.

---

# 11. Expectation

Discrete:

`E[X] = Σ x pX(x)`

Continuous:

`E[X] = ∫ x fX(x) dx`

### Example

Fair die:

`E[X]=(1+2+3+4+5+6)/6 = 3.5`

Expected value does not have to be an outcome that can actually occur.

---

# 12. Linearity of Expectation

One of the most important quant tools:

`E[X+Y]=E[X]+E[Y]`

More generally:

`E[Σ Xᵢ] = Σ E[Xᵢ]`

**Independence is NOT required.**

### Example

100 dice:

`E[sum] = 100 × 3.5 = 350`

No enumeration of `6^100` outcomes is needed.

---

# 13. Indicator Variables

Define:

`I_A = 1` if A happens, otherwise `0`.

Then:

`E[I_A]=P(A)`

This turns counting problems into expectation problems.

### Example

Roll 100 dice.

Let `Iᵢ=1` if die i is a six.

`E[Iᵢ]=1/6`

Number of sixes:

`X=I₁+...+I₁₀₀`

Therefore:

`E[X]=100/6 = 50/3`

---

# 14. LOTUS

Law of the Unconscious Statistician:

`E[g(X)] = Σ g(x)pX(x)`

or continuously:

`E[g(X)] = ∫ g(x)fX(x) dx`

Example:

For a fair die:

`E[X²]=(1²+2²+...+6²)/6 = 91/6`

---

# 15. Variance

Definition:

`Var(X)=E[(X-E[X])²]`

Useful computational formula:

`Var(X)=E[X²]-(E[X])²`

Example for a fair die:

`E[X]=3.5`

`E[X²]=91/6`

so:

`Var(X)=91/6 - 3.5² = 35/12`

## Standard deviation

`SD(X)=√Var(X)`

---

# 16. Scaling

`E[aX+b]=aE[X]+b`

`Var(aX+b)=a²Var(X)`

Adding a constant does not change variance.

---

# 17. Covariance

`Cov(X,Y)=E[(X-E[X])(Y-E[Y])]`

Equivalent:

`Cov(X,Y)=E[XY]-E[X]E[Y]`

## Correlation

`Corr(X,Y)=Cov(X,Y)/[SD(X)SD(Y)]`

Always:

`-1 ≤ Corr(X,Y) ≤ 1`

---

# 18. Variance of a Sum

`Var(X+Y)=Var(X)+Var(Y)+2Cov(X,Y)`

If independent:

`Var(X+Y)=Var(X)+Var(Y)`

For many variables:

`Var(ΣXᵢ)=ΣVar(Xᵢ)+2Σᵢ<ⱼ Cov(Xᵢ,Xⱼ)`

---

# 19. Bernoulli Distribution

One success/failure trial.

`X ~ Bernoulli(p)`

`P(X=1)=p`

`P(X=0)=1-p`

Mean:

`E[X]=p`

Variance:

`Var(X)=p(1-p)`

---

# 20. Binomial Distribution

Number of successes in n independent Bernoulli trials.

`X ~ Binomial(n,p)`

`P(X=k)=C(n,k)p^k(1-p)^(n-k)`

Mean:

`E[X]=np`

Variance:

`Var(X)=np(1-p)`

### Example

Exactly 6 heads in 10 fair flips:

`P(X=6)=C(10,6)(1/2)^10 = 210/1024`

---

# 21. Geometric Distribution

Number of trials until the first success.

`X ~ Geometric(p)`

`P(X=k)=(1-p)^(k-1)p`

Mean:

`E[X]=1/p`

Variance:

`Var(X)=(1-p)/p²`

### Example

If success probability is 0.2:

`E[X]=1/0.2=5`

---

# 22. Memorylessness

Geometric distribution:

`P(X>s+t | X>s)=P(X>t)`

Interpretation:

> How long you have already waited does not affect the future waiting time.

Exponential distributions have the same memoryless property.

---

# 23. Negative Binomial

Number of trials until the r-th success:

`P(X=k)=C(k-1,r-1)p^r(1-p)^(k-r)`

Mean:

`E[X]=r/p`

Variance:

`Var(X)=r(1-p)/p²`

---

# 24. Hypergeometric

Use for sampling **without replacement**.

Population:

- N total
- K successes
- n draws
- k successes wanted

`P(X=k)=C(K,k)C(N-K,n-k)/C(N,n)`

Example: 5 cards from a 52-card deck, exactly 2 hearts:

`C(13,2)C(39,3)/C(52,5)`

Contrast:

- Binomial → independent trials / with replacement
- Hypergeometric → without replacement

---

# 25. Poisson

For counts of events at rate λ:

`P(X=k)=e^(-λ) λ^k/k!`

Mean:

`E[X]=λ`

Variance:

`Var(X)=λ`

## Poisson approximation

If n is large, p is small, and `np=λ`:

`Binomial(n,p) ≈ Poisson(λ)`

---

# 26. Uniform Distribution

`X ~ Uniform(a,b)`

Density:

`f(x)=1/(b-a)`

Mean:

`E[X]=(a+b)/2`

Variance:

`Var(X)=(b-a)²/12`

---

# 27. Exponential Distribution

`X ~ Exponential(λ)`

Density:

`f(x)=λe^(-λx)`

CDF:

`F(x)=1-e^(-λx)`

Mean:

`E[X]=1/λ`

Variance:

`Var(X)=1/λ²`

Memoryless:

`P(X>s+t|X>s)=P(X>t)`

Think:

- Geometric = discrete waiting time
- Exponential = continuous waiting time

---

# 28. Normal Distribution

`X ~ N(μ,σ²)`

Mean:

`E[X]=μ`

Variance:

`Var(X)=σ²`

Standardization:

`Z=(X-μ)/σ`

## 68–95–99.7 rule

Approximately:

- within 1σ → 68%
- within 2σ → 95%
- within 3σ → 99.7%

Memorize these.

---

# 29. Beta Distribution

`X ~ Beta(α,β)`

Mean:

`E[X]=α/(α+β)`

Variance:

`Var(X)=αβ/[(α+β)²(α+β+1)]`

Useful for variables representing probabilities between 0 and 1.

---

# 30. Gamma Distribution

Using shape α and rate λ:

`X ~ Gamma(α,λ)`

Mean:

`E[X]=α/λ`

Variance:

`Var(X)=α/λ²`

Special case:

`Gamma(1,λ)=Exponential(λ)`

---

# 31. Joint Distributions

Joint PMF:

`pX,Y(x,y)=P(X=x,Y=y)`

Marginal:

`pX(x)=Σ_y pX,Y(x,y)`

Conditional:

`P(X=x|Y=y)=pX,Y(x,y)/pY(y)`

Independence:

`pX,Y(x,y)=pX(x)pY(y)`

---

# 32. Conditional Expectation

`E[X|Y=y]=Σ_x x P(X=x|Y=y)`

Interpretation:

> Expected X after learning Y=y.

---

# 33. Law of Total Expectation

`E[X]=E[E[X|Y]]`

Example:

Group A = 60%, average 50k.

Group B = 40%, average 80k.

Overall:

`E[X]=0.6(50000)+0.4(80000)=62000`

---

# 34. Law of Total Variance

`Var(X)=E[Var(X|Y)] + Var(E[X|Y])`

Interpretation:

**Total variation = average within-group variation + variation between group means.**

---

# 35. Multinomial

Generalization of binomial.

`P(X₁=x₁,...,Xₖ=xₖ)`

`= n!/(x₁!...xₖ!) × p₁^x₁...pₖ^xₖ`

where:

`Σxᵢ=n`

and:

`Σpᵢ=1`

---

# 36. Transformations

If:

`Y=g(X)`

For a monotonic continuous transformation:

`fY(y)=fX(g⁻¹(y)) |d/dy g⁻¹(y)|`

Start by mastering simple transformations:

- `Y=aX+b`
- `Y=X²`
- `Y=e^X`
- `Y=ln X`

---

# 37. Lognormal

If:

`X ~ N(μ,σ²)`

then:

`Y=e^X`

is lognormal.

Mean:

`E[Y]=e^(μ+σ²/2)`

Variance:

`Var(Y)=(e^(σ²)-1)e^(2μ+σ²)`

---

# 38. Moment Generating Function

`M_X(t)=E[e^(tX)]`

Moments:

`M'_X(0)=E[X]`

`M''_X(0)=E[X²]`

More generally:

`M_X^(n)(0)=E[X^n]`

If X and Y are independent:

`M_(X+Y)(t)=M_X(t)M_Y(t)`

---

# 39. Convolution

For independent continuous X,Y and `Z=X+Y`:

`fZ(z)=∫ fX(x)fY(z-x) dx`

Discrete:

`P(Z=z)=Σ_x P(X=x)P(Y=z-x)`

---

# 40. Inequalities

## Cauchy-Schwarz

`(E[XY])² ≤ E[X²]E[Y²]`

## Markov

For X ≥ 0:

`P(X≥a) ≤ E[X]/a`

Example: If E[X]=2:

`P(X≥10) ≤ 0.2`

## Chebyshev

`P(|X-μ|≥kσ) ≤ 1/k²`

For k=2:

`P(|X-μ|≥2σ) ≤ 1/4`

## Jensen

For convex f:

`f(E[X]) ≤ E[f(X)]`

For concave f, reverse the inequality.

---

# 41. Law of Large Numbers

For iid variables with mean μ:

`X̄_n → μ`

as `n → ∞`.

Meaning:

> As the sample size grows, the sample average approaches the true mean.

---

# 42. Central Limit Theorem

For iid variables with mean μ and variance σ²:

`(X̄-μ)/(σ/√n) → N(0,1)`

for large n.

Approximately:

`X̄ ~ N(μ, σ²/n)`

This explains why normal approximations appear so often.

---

# 43. Markov Chains

Markov property:

`P(X_(t+1)|X_t,X_(t-1),...) = P(X_(t+1)|X_t)`

Meaning:

> The future depends on the present, not the full history.

## Transition matrix

`P_ij=P(X_(t+1)=j | X_t=i)`

Every row sums to 1.

## Multi-step transition

`P^(n)=P^n`

---

# 44. Stationary Distribution

A distribution π is stationary if:

`πP=π`

and:

`Σπ_i=1`

Interpretation:

> Applying the transition does not change the distribution.

## Detailed balance

`π_i P_ij = π_j P_ji`

---

# 45. Hitting Times and First-Step Analysis

Let:

`T_A=min{t≥0 : X_t ∈ A}`

be the first time we reach A.

If `E_i` is the expected time to reach the target from state i:

`E_i = 1 + Σ_j P_ij E_j`

with:

`E_target=0`

### Example

You are one step away from a target.

With probability 1/2 you reach it.

With probability 1/2 you return to the starting point.

Let E be the expected time:

`E = 1 + (1/2)(0) + (1/2)E`

Therefore:

`E/2=1`

`E=2`

The `1` represents the step just taken.

---

# 46. Quant Interview Tricks

## Trick 1 — Linearity of expectation

If asked for expected total:

`E[X₁+...+X_n]`

immediately split it:

`E[X₁]+...+E[X_n]`

Do not enumerate every outcome.

## Trick 2 — Indicators

If asked:

> Expected number of occurrences?

Try:

`X=ΣI_i`

Then:

`E[X]=ΣP(I_i=1)`

## Trick 3 — Complement

If asked:

> Probability of at least one?

Use:

`P(at least one)=1-P(none)`

## Trick 4 — First-step analysis

For random walks/games:

`E=1+ΣP_iE_i`

## Trick 5 — Condition

If direct calculation is difficult:

`P(A)=ΣP(A|B_i)P(B_i)`

or:

`E[X]=E[E[X|Y]]`

## Trick 6 — Symmetry

Look for paired/symmetric outcomes before calculating.

For a symmetric uniform interval:

`E[X]=(lower+upper)/2`

---

# 47. Distribution Cheat Sheet

| Distribution | Typical use | Mean | Variance |
|---|---|---:|---:|
| Bernoulli(p) | One success/failure | p | p(1-p) |
| Binomial(n,p) | # successes in n trials | np | np(1-p) |
| Geometric(p) | Trials until success | 1/p | (1-p)/p² |
| Negative Binomial | Trials until r successes | r/p | r(1-p)/p² |
| Hypergeometric | Sampling without replacement | — | — |
| Poisson(λ) | Count of rare events | λ | λ |
| Uniform(a,b) | Equal density interval | (a+b)/2 | (b-a)²/12 |
| Exponential(λ) | Continuous waiting time | 1/λ | 1/λ² |
| Normal(μ,σ²) | Bell-shaped continuous variable | μ | σ² |
| Beta(α,β) | Random probability | α/(α+β) | αβ/[(α+β)²(α+β+1)] |
| Gamma(α,λ) | Waiting time / sums of exponentials | α/λ | α/λ² |

---

# 48. What to Memorize First

## Tier 1 — Absolute priority

Memorize:

`P(A|B)=P(A∩B)/P(B)`

`P(A∩B)=P(A|B)P(B)`

`P(A|B)=P(B|A)P(A)/P(B)`

`P(B)=ΣP(B|A_i)P(A_i)`

`E[X]=Σxp(x)`

`E[X+Y]=E[X]+E[Y]`

`E[I_A]=P(A)`

`Var(X)=E[X²]-(E[X])²`

`Cov(X,Y)=E[XY]-E[X]E[Y]`

`Var(X+Y)=Var(X)+Var(Y)+2Cov(X,Y)`

`E[X]=E[E[X|Y]]`

`Var(X)=E[Var(X|Y)]+Var(E[X|Y])`

## Tier 2

Memorize:

- Binomial PMF and mean/variance
- Geometric PMF and mean
- Hypergeometric PMF
- Poisson PMF
- Exponential density and mean
- Normal standardization

## Tier 3

Learn after the above:

- MGF
- Convolution
- Transformations
- Beta/Gamma
- Cauchy-Schwarz
- Markov
- Chebyshev
- Jensen
- LLN
- CLT
- Markov chains

---

# 49. Study Loop

For every concept:

```text
Learn
  ↓
Write formula from memory
  ↓
Solve 1 easy example
  ↓
Solve 5 basic problems
  ↓
Solve 5 mixed problems
  ↓
Solve 1 hard interview problem
  ↓
Explain solution aloud
  ↓
Review mistakes after 2 days
  ↓
Review again after 1 week
```

The important progression is:

```text
"I know the formula"
        ↓
"I know when to use it"
        ↓
"I recognize the structure without being told"
```

The final stage is what matters for quantitative-trading interviews.

---

# 50. Minimum Mastery Checklist

Before moving beyond Stat 110, you should be comfortable with:

- [ ] Counting
- [ ] Permutations
- [ ] Combinations
- [ ] Inclusion-exclusion
- [ ] Conditional probability
- [ ] Bayes
- [ ] Total probability
- [ ] Independence
- [ ] Conditional independence
- [ ] Expected value
- [ ] Linearity of expectation
- [ ] Indicator variables
- [ ] Variance
- [ ] Covariance
- [ ] Conditional expectation
- [ ] Binomial
- [ ] Geometric
- [ ] Hypergeometric
- [ ] Poisson
- [ ] Exponential
- [ ] Normal
- [ ] Joint distributions
- [ ] LOTUS
- [ ] Total expectation
- [ ] Total variance
- [ ] Markov/Chebyshev/Jensen
- [ ] LLN
- [ ] CLT
- [ ] Markov chains
- [ ] Random walks
- [ ] Hitting times
- [ ] First-step analysis

---

# 51. The Ten Questions to Ask on a New Quant Problem

When you see an unfamiliar probability problem, ask:

1. **Can I count it?**
2. **Can I use symmetry?**
3. **Can I use the complement?**
4. **Should I condition on something?**
5. **Can I use Bayes?**
6. **Can I use linearity of expectation?**
7. **Can I introduce indicators?**
8. **Can I condition on the first step?**
9. **Is there a memoryless property?**
10. **Is this a Markov chain?**

These questions are often more useful than memorizing another formula.

---

# Recommended learning order

Week 1:
- Counting
- Conditional probability
- Bayes
- Independence
- Total probability

Week 2:
- Random variables
- Expectation
- Indicators
- Variance
- Covariance

Week 3:
- Bernoulli
- Binomial
- Geometric
- Hypergeometric
- Poisson
- Exponential
- Normal

Week 4:
- Joint distributions
- Conditional expectation
- Total expectation
- Total variance
- Inequalities

Week 5:
- LLN
- CLT
- Markov chains
- Random walks
- Hitting times
- First-step analysis

For quant trading, spend extra practice time on **counting, conditional probability, expected value, indicators, conditional expectation, random walks, and first-step analysis**. These are especially high-value interview skills.
