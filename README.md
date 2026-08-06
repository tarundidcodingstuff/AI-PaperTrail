https://www.youtube.com/watch?v=kLJEXE5_7rI&t=451s    - Quant Roadmap

# AI-PaperTrail
My working log of AI papers, projects, and experiments.


Yes — and after reading both your resume and the Anthropic RL Fellows description, I think the right way to approach this is **not** “learn every part of AI before applying.”

Your strongest route is:

**Software Engineer → ML Engineer → Research Engineer**

rather than trying to turn yourself immediately into a theoretical Research Scientist.

Your current CV already gives you something valuable: several years of real software engineering, distributed systems, Python/.NET interoperability, gRPC/TCP, debugging production systems, plus two increasingly research-oriented AutoML projects.  

What you're missing is primarily **modern deep-learning/RL depth, experimental research practice, LLM training/evaluation experience, and evidence that you can independently investigate a research question.**

## First: you're closer to the Anthropic Fellowship than you think

The Fellowship is explicitly intended to develop research and engineering talent “regardless of previous experience,” and fellows work on a four-month empirical project intended to produce a public research output. 

More importantly, look at what the RL workstream actually asks for. It highlights people who have strong software engineering skills, can build complex ML systems, balance research exploration with engineering rigor, work with distributed/HPC systems, train/fine-tune/evaluate LLMs, and debug model training. 

Against that:

| Anthropic RL Fellow signal  | You today                 |
| --------------------------- | ------------------------- |
| Strong software engineering | **Strong**                |
| Python                      | **Good, improve fluency** |
| Distributed systems         | **Strong**                |
| Implement ideas quickly     | **Strong potential**      |
| Classical ML                | **Moderate**              |
| PyTorch                     | **Beginner–intermediate** |
| Transformers                | **Weak currently**        |
| LLM training                | **Gap**                   |
| Fine-tuning                 | **Gap**                   |
| RL fundamentals             | **Major gap**             |
| Deep RL                     | **Major gap**             |
| RL for LLMs                 | **Major gap**             |
| Evaluation                  | **Some experience**       |
| Research methodology        | **Gap**                   |
| Reading papers              | **Gap**                   |
| Reproducing papers          | **Gap**                   |
| Published research          | **None yet**              |
| ML systems                  | **Developing**            |

That's actually a workable starting position.

And the projects Anthropic describes include creating RL environments, investigating generalization, training-data tooling, safety environments, and implementing RL algorithms. 

So I wouldn't tell you to wait two years.

I would spend the next **6–12 months deliberately transforming your profile**.

---

# Your target

Don't optimize solely for:

> “Get Anthropic Fellowship.”

Optimize for:

> **Become a strong Research Engineer candidate who happens to apply to Anthropic/OpenAI.**

That gives you many more possible outcomes.

Anthropic currently lists numerous Research Engineer positions across RL, RL Scaling Science, RL Velocity, model evaluations, pretraining, interpretability and post-training. ([Anthropic][1])

And [OpenAI's general Research Engineer role](https://openai.com/careers/research-engineer-san-francisco/?utm_source=chatgpt.com) emphasizes strong programming and large distributed systems — unusually compatible with your existing professional background.

The specific [OpenAI RL/Reasoning Research Engineer/Scientist role](https://openai.com/careers/research-engineerresearch-scientist-rlreasoning-san-francisco/?utm_source=chatgpt.com) then adds the missing component: RL research and rapid experimentation.

So there is a very obvious bridge:

**Your SWE experience → serious ML engineering → RL/LLM experimentation → research engineering.**

---

# Phase 0 — Change how you're learning

This is probably the most important change.

Don't spend six months doing:

```text
Course
↓
Course
↓
Course
↓
Tutorial
↓
Certificate
↓
Apply to Anthropic
```

Instead use:

```text
Learn
 ↓
Implement
 ↓
Experiment
 ↓
Read relevant paper
 ↓
Reproduce result
 ↓
Change something
 ↓
Measure it
 ↓
Write findings
 ↓
GitHub
```

That's the beginning of research.

You said you **don't know how to research**.

That's okay. Research isn't something you need to magically know before starting.

You can learn the process.

---

# Phase 1 — 6–8 weeks: build your foundations

You already know some ML. Don't restart from linear regression.

## Mathematics

You need working understanding of:

**Linear algebra**

Vectors, matrices, matrix multiplication, eigenvalues/eigenvectors, SVD, norms, projections.

**Probability**

Random variables, expectation, variance, conditional probability, Bayes rule, common distributions, likelihood, KL divergence, entropy, cross-entropy.

**Optimization**

Gradient descent, SGD, momentum, Adam/AdamW, learning-rate schedules, regularization.

You don't need mathematician-level proof ability.

You need to be able to look at something like

[
L(\theta)=-E[\log p_\theta(y|x)]
]

and understand what is being optimized and implement it.

Algebra & Functions — equations, functions, logarithms, exponentials, summations.
Linear Algebra ⭐⭐⭐⭐⭐ — vectors, matrices, tensors, eigenvalues, SVD, projections, norms.
Calculus ⭐⭐⭐⭐⭐ — derivatives, integrals, chain rule.
Multivariable Calculus ⭐⭐⭐⭐⭐ — partial derivatives, gradients, Jacobians, Hessians.
Probability Theory ⭐⭐⭐⭐⭐ — random variables, distributions, expectation, variance, conditional probability, Bayes.
Statistics ⭐⭐⭐⭐⭐ — estimation, sampling, confidence intervals, hypothesis testing, experimental analysis.
Information Theory ⭐⭐⭐⭐⭐ — entropy, cross-entropy, KL divergence, mutual information, perplexity.
Mathematical Optimization ⭐⭐⭐⭐⭐ — gradient descent, SGD, momentum, Adam/AdamW, convexity, constrained optimization.
Numerical Methods / Numerical Computing ⭐⭐⭐⭐ — floating point, numerical stability, approximation, FP16/BF16, stable softmax/log computations.
Bayesian Statistics & Bayesian Inference ⭐⭐⭐ — priors, likelihoods, posteriors, MLE/MAP, Gaussian processes, Bayesian optimization.
Stochastic Processes ⭐⭐⭐⭐ — Markov chains, Markov processes, expectations over trajectories; particularly important for RL.
Reinforcement Learning Mathematics ⭐⭐⭐⭐⭐ — MDPs, Bellman equations, value functions, policy gradients, importance sampling, advantage estimation.
Optimization for RL ⭐⭐⭐⭐⭐ — policy gradients, PPO objectives, KL constraints, trust regions, entropy regularization.
Matrix Calculus ⭐⭐⭐⭐ — derivatives involving vectors/matrices, useful for understanding backpropagation and papers.
Discrete Mathematics ⭐⭐⭐ — sets, relations, combinatorics, graphs, logic; useful but lower priority for your immediate ML path.


---

# Phase 2 — Become extremely comfortable with PyTorch

This is more important for your target than learning ten ML libraries.

Your goal should be:

> Give Tarun a paper containing a model architecture and he can implement a simplified version.

You should be able to build without following a tutorial:

```text
Dataset / DataLoader
        ↓
Model
        ↓
Forward pass
        ↓
Loss
        ↓
Backward
        ↓
Optimizer
        ↓
Training loop
        ↓
Validation
        ↓
Checkpointing
        ↓
Metrics
        ↓
Experiment logging
```

Then implement manually:

```text
Linear regression
MLP
CNN
RNN/LSTM
Attention
Multi-head attention
Transformer block
Small Transformer
```

The last three matter enormously.

---

# Phase 3 — Build a Transformer from scratch

I would make this one of your next major GitHub projects.

Not:

> “Fine-tuned BERT using HuggingFace.”

Instead:

### `mini-transformer`

Implement:

```text
Tokenizer
   ↓
Token embeddings
   +
Positional information
   ↓
Multi-Head Self Attention
   ↓
Residual
   ↓
LayerNorm
   ↓
MLP
   ↓
Residual
   ↓
LayerNorm
   ↓
LM Head
```

Train a small autoregressive language model.

Understand:

[
Q=XW_Q,\quad K=XW_K,\quad V=XW_V
]

and

[
Attention(Q,K,V)
================

softmax\left(\frac{QK^T}{\sqrt{d_k}}\right)V
]

Don't just memorize it.

Ask:

**Why divide by (\sqrt{d_k})?**

**Why causal masking?**

**Why multiple heads?**

**Pre-norm vs post-norm?**

**What happens if I change context length?**

**Why does training diverge?**

That questioning mindset is where research starts.

---

# Phase 4 — Learn RL properly

For the Anthropic workstream you showed me, this is currently your biggest knowledge gap.

Learn in this order:

```text
Markov Decision Processes
        ↓
State / Action / Reward
        ↓
Policy
        ↓
Return
        ↓
Value Functions
        ↓
Bellman Equations
        ↓
Dynamic Programming
        ↓
Monte Carlo
        ↓
Temporal Difference Learning
        ↓
Q-Learning
        ↓
DQN
        ↓
Policy Gradients
        ↓
REINFORCE
        ↓
Actor-Critic
        ↓
PPO
```

Do **not** jump directly to RLHF.

Implement several algorithms yourself.

I'd target:

### Project 1

`rl-from-scratch`

Implement:

```text
Q-learning
DQN
REINFORCE
Actor-Critic
PPO
```

Use small environments.

Your README should contain experiments:

```text
Algorithm     Environment     Mean Reward
DQN           CartPole        ...
REINFORCE     CartPole        ...
PPO           LunarLander     ...
```

Then investigate something.

For example:

> How does PPO clipping affect training stability?

Now you have a research question.

---

# Phase 5 — Learn LLM post-training

This is where your profile starts becoming relevant to frontier labs.

Learn:

```text
Pretraining
    ↓
Supervised Fine-Tuning
    ↓
Preference Data
    ↓
Reward Modeling
    ↓
RLHF
    ↓
PPO
```

Then modern approaches:

```text
DPO
RLAIF
GRPO-style methods
Verifiable rewards
RL environments
Reasoning RL
Synthetic feedback
```

You don't need to train a 70B model.

Use tiny models.

For example:

```text
Qwen 0.5B
SmolLM
TinyLlama
```

Build:

### `mini-rlhf`

Something like:

```text
Base LM
 ↓
SFT
 ↓
Preference Dataset
 ↓
Reward Model
 ↓
PPO/DPO
 ↓
Evaluation
```

Even a simplified implementation would change the character of your CV considerably.

---

# Phase 6 — Learn to read papers

You specifically said:

> I don't know how to read papers.

Don't read them like textbooks.

First pass — **10 minutes**:

```text
Abstract
Introduction
Figures
Conclusion
```

Answer only:

> What problem are they solving?

> What is their idea?

> What did they compare against?

> Did it work?

Then second pass:

```text
Method
Experiments
Ablations
```

Then third pass only if important:

```text
Equations
Appendix
Implementation details
```

Create a markdown file for every important paper:

```text
# Paper

## Problem

## Main idea

## Method

## Experimental setup

## Results

## What surprised me?

## Weaknesses

## Questions

## What would I test next?

## Can I reproduce it?
```

That last question is crucial.

---

# Then reproduce papers

Start easy.

Don't choose a 400-GPU frontier experiment.

Do something like:

```text
Paper
 ↓
Understand method
 ↓
Find manageable dataset/environment
 ↓
Implement/reproduce
 ↓
Compare your result
 ↓
Explain discrepancy
```

Then modify **one variable**.

Example:

> Original PPO uses clipping ε = 0.2.

Run:

```text
ε = 0.05
ε = 0.1
ε = 0.2
ε = 0.3
ε = 0.5
```

Plot:

```text
Reward
   |
   |       ______ ε=.2
   |     /
   |   /
   |__/_____________
       Training Steps
```

Then explain what happened.

Congratulations — you're doing a small empirical research project.

---

# Your PFN project can become your first real research training ground

This is why I like the direction of your PFN project.

Right now your resume says you converted NanoTabPFN toward regression, used Gaussian NLL/variance, constructed real/synthetic trials and attempted to predict whether configurations deserve further training. 

Don't stop at:

> “I built this.”

Turn it into:

> **“I investigated whether this works.”**

That's a completely different level.

Run:

```text
Random Search
Optuna TPE
Random Forest surrogate
XGBoost surrogate
Gaussian Process
NanoTabPFN
PFN + KNN context
PFN + synthetic prior
```

Then measure:

```text
Best R² after N evaluations
Regret
Wall-clock time
Skipped evaluations
Surrogate RMSE
Ranking correlation
Uncertainty calibration
```

Do ablations:

```text
No synthetic data
vs
Synthetic data

No retrieval
vs
KNN retrieval

k=8
k=16
k=32
k=64

No uncertainty
vs
Uncertainty-aware selection
```

Then write a **6–8 page research-style report**.

Even if the result is:

> PFN did not outperform Random Forest.

That is still useful research experience if the experiment is rigorous.

---

# Then build one project directly aligned with Anthropic RL

Anthropic explicitly mentions building RL environments, investigating generalization, safety-related environments and RL algorithms. 

So I'd make your next project something like:

## `LLM-RL-Generalization-Lab`

Question:

> **Does RL training on procedurally generated reasoning environments improve out-of-distribution generalization?**

Build generated tasks:

```text
Arithmetic
Logic
Planning
Symbolic manipulation
```

Generate:

```text
Training environments
        ↓
Difficulty 1–5

OOD environments
        ↓
Difficulty 6–10
```

Train a small model.

Compare:

```text
SFT
vs
RL
vs
SFT + RL
```

Evaluate:

```text
In-distribution accuracy
OOD accuracy
Reward
Generalization gap
Training stability
```

Now your GitHub begins telling a coherent story:

```text
PFN AutoML
     ↓
Optimization / uncertainty / experimentation

Mamba AutoML
     ↓
Architecture search

RL From Scratch
     ↓
RL fundamentals

Transformer From Scratch
     ↓
LLM fundamentals

LLM RL Generalization
     ↓
Actual research question
```

That is far stronger than 15 unrelated Kaggle projects.

---

# Your software-engineering background is an advantage

Don't throw away your previous career because you're moving toward ML.

Your resume already shows distributed task execution, gRPC/TCP, static analysis, production debugging, .NET/Python integration and systems serving thousands of users.  

Research engineering needs people who can make experiments actually work.

And OpenAI's current general Research Engineer description explicitly emphasizes engineering massive-scale distributed ML systems and strong programming. ([OpenAI][2])

That's why I'd lean toward **Research Engineer rather than Research Scientist** as your long-term target.

---

# A realistic 12-month transformation

| Months | Main focus              | Deliverable                |
| ------ | ----------------------- | -------------------------- |
| 1–2    | Math + PyTorch + DL     | DL implementations         |
| 2–3    | Transformers            | Transformer from scratch   |
| 3–4    | RL foundations          | Q-learning → PPO           |
| 4–5    | Papers + experiments    | 5 reproductions            |
| 5–6    | LLM training            | Fine-tuning project        |
| 6–7    | RLHF/DPO/PPO            | Mini post-training stack   |
| 7–8    | PFN research            | Proper experimental report |
| 8–10   | LLM + RL research       | Original empirical project |
| 10–11  | Research writing        | Technical report/preprint  |
| 11–12  | Applications/interviews | Anthropic/OpenAI/etc.      |

You should be reading papers throughout this entire process rather than waiting until month 4.

Aim initially for **2 papers/week**, not 20.

---

# What your profile should eventually look like

Today:

```text
Software Engineer
       +
Some ML
       +
Interesting AutoML projects
```

Target:

```text
              Research Engineer
                     │
        ┌────────────┼────────────┐
        │            │            │
   Engineering      ML        Research
        │            │            │
 Distributed       PyTorch     Papers
 Systems           LLMs        Experiments
 Python            RL          Ablations
 Debugging         HPO         Reproduction
 Performance       Training    Evaluation
        │            │            │
        └────────────┼────────────┘
                     │
             LLM / RL Systems
```

That combination is valuable.

---

# One important issue with this particular Fellowship

There is a practical constraint independent of your technical preparation.

The attached Anthropic posting says Fellows must have **full-time work authorization in the US, UK, or Canada**, must be located there during the program, and Anthropic **does not currently sponsor visas for Fellows**. 

So depending on your work authorization, this particular Fellowship may or may not be feasible even if you're technically accepted.

That's different from Anthropic's full-time roles; the posting says their full-time-role visa policy is different and sponsorship can be available. 

So **don't structure your entire career around admission to this one program**.

For OpenAI, also keep an eye on [OpenAI Emerging Talent](https://openai.com/careers/emerging-talent/?utm_source=chatgpt.com) and the Residency pathway in addition to regular Research Engineer roles.

---

# What I would do starting tomorrow

Don't start with another big AutoML project.

For the next month:

1. **PyTorch deeply**
2. **Transformer from scratch**
3. **Start RL from Sutton & Barto / practical implementations**
4. **Read 2 papers each week**
5. **Finish the PFN experiments rigorously**
6. Write everything publicly on GitHub.

After that:

**DQN → REINFORCE → PPO → LLM fine-tuning → DPO/RLHF → RL environments → independent experiment.**

And while doing your MSc, actively look for a **HiWi / research assistant / thesis position in an ML research group**. Having a professor teach you how research actually happens would accelerate this dramatically.

The end goal isn't to make your resume *say*:

> Reinforcement Learning, Transformers, LLMs, RLHF.

It's to get you to the point where an Anthropic/OpenAI interviewer can ask:

> “Why did PPO training become unstable in experiment 17?”

and you can spend twenty minutes discussing what you observed, what you hypothesized, what diagnostics you ran, what you changed, and what the evidence showed.

**That's the Research Engineer you're trying to become.**

If you want, I can next build you a **very concrete 6-month “Anthropic/OpenAI Research Engineer curriculum”** — week by week, including exactly what math to learn, which papers to read, what to implement, 4–5 GitHub projects, and when to start applying.

[1]: https://www.anthropic.com/careers/jobs?gh_src=Simplify&utm_source=chatgpt.com "Jobs \ Anthropic"
[2]: https://openai.com/careers/research-engineer-san-francisco/?utm_source=chatgpt.com "Research Engineer | OpenAI"
