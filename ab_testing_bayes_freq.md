# Bayesian and Frequentist Approaches to A/B Testing

## 1. Problem Setup  

We run an **A/B test** to compare two variants (say, website versions A and B).  

Let  
- \(n_A, n_B\) = number of users exposed to A and B.  
- \(x_A, x_B\) = number of “successes” (e.g. clicks, purchases).  
- \(\hat{p}_A = x_A / n_A,\; \hat{p}_B = x_B / n_B\) = observed sample proportions.  

We want to infer something about the **true conversion rates** \(p_A, p_B\).  

---

## 2. Frequentist Approach  

### Hypotheses  
We test  
\[
H_0: p_A = p_B \quad 	ext{vs.} \quad H_1: p_A 
eq p_B.
\]  

Or sometimes one-sided: \(H_1: p_B > p_A\).  

### Test Statistic  
The difference in sample proportions:  
\[
\hat{d} = \hat{p}_B - \hat{p}_A.
\]  

Under the null, the test statistic (approximate Z-score) is:  

\[
Z = rac{\hat{p}_B - \hat{p}_A}{\sqrt{\hat{p}(1-\hat{p})(\tfrac{1}{n_A}+\tfrac{1}{n_B})}},
\]  

where \(\hat{p} = rac{x_A+x_B}{n_A+n_B}\) is the **pooled estimate** under \(H_0\).  

### Inference  
- Compute \(Z\).  
- Compare to critical values from standard normal, or compute \(p\)-value:  
\[
p	ext{-value} = \mathbb{P}(|Z| > |z_{	ext{obs}}| \mid H_0).
\]  

- Reject \(H_0\) if \(p < lpha\) (e.g., 0.05).  

### Confidence Interval (CI) for difference  
\[
\hat{d} \pm z_{1-lpha/2} \cdot \sqrt{rac{\hat{p}_A(1-\hat{p}_A)}{n_A} + rac{\hat{p}_B(1-\hat{p}_B)}{n_B}}.
\]  

---

## 3. Bayesian Approach  

### Likelihood  
For each group:  
\[
x_A \sim 	ext{Binomial}(n_A, p_A), \quad x_B \sim 	ext{Binomial}(n_B, p_B).
\]  

### Priors  
Choose priors for \(p_A, p_B\). A common choice:  
\[
p_A \sim 	ext{Beta}(lpha_A, eta_A), \quad p_B \sim 	ext{Beta}(lpha_B, eta_B).
\]  

If uninformative: \(	ext{Beta}(1,1)\) (uniform).  

### Posteriors  
By conjugacy:  
\[
p_A \mid 	ext{data} \sim 	ext{Beta}(lpha_A + x_A, eta_A + n_A - x_A),
\]  
\[
p_B \mid 	ext{data} \sim 	ext{Beta}(lpha_B + x_B, eta_B + n_B - x_B).
\]  

### Inference  
We want posterior probability that B is better than A:  
\[
\Pr(p_B > p_A \mid 	ext{data}).
\]  

This generally requires simulation (Monte Carlo): draw many samples from the two posteriors and compute the proportion of draws with \(p_B > p_A\).  

Also, we can compute **credible intervals**:  
- 95% CI = interval covering 95% posterior probability mass.  

### Decision Making  
- If \(\Pr(p_B > p_A \mid 	ext{data}) > 0.95\), declare B better.  
- Or use **expected loss/utility** if costs of wrong decisions differ.  

---

## 4. Key Comparison  

| Aspect | Frequentist | Bayesian |
|--------|-------------|----------|
| Model of uncertainty | Randomness in data, parameters fixed | Parameters are random variables with distributions |
| Output | \(p\)-value, confidence interval | Posterior distribution, credible interval |
| Hypothesis | Tests \(H_0\) vs. \(H_1\) | Computes probability of hypotheses |
| Example interpretation | “If \(H_0\) is true, probability of data this extreme is 0.03” | “Probability that \(p_B > p_A\) given data is 0.97” |
| Computation | Closed-form Z-tests | Often simulation (MCMC or sampling) |

---

## 5. Worked Example  

Suppose  
- \(n_A = n_B = 1000\),  
- \(x_A = 120\),  
- \(x_B = 150\).  

### Frequentist Analysis  
\[
\hat{p}_A = 0.12, \quad \hat{p}_B = 0.15, \quad \hat{d} = 0.03.
\]  

Pooled estimate:  
\[
\hat{p} = rac{120+150}{2000} = 0.135.
\]  

Standard error:  
\[
SE = \sqrt{0.135 	imes 0.865 	imes \left(	frac{1}{1000}+	frac{1}{1000}ight)} pprox 0.015.
\]  

Z-score:  
\[
Z = rac{0.03}{0.015} = 2.0.
\]  

\(p\)-value (two-tailed) \(pprox 0.045\).  
→ At \(lpha=0.05\), we **just reject** \(H_0\).  

### Bayesian Analysis  
Use uniform priors: \(	ext{Beta}(1,1)\).  

Posterior distributions:  
\[
p_A \sim 	ext{Beta}(121, 881), \quad p_B \sim 	ext{Beta}(151, 851).
\]  

Monte Carlo draws give:  
- \(\Pr(p_B > p_A \mid 	ext{data}) pprox 0.975\).  
- 95% credible interval for difference roughly \([0.002, 0.058]\).  

→ Bayesian result gives **stronger evidence** that B is better.  

---

# Summary  

- **Frequentist A/B testing**: relies on null hypothesis testing, \(p\)-values, confidence intervals.  
- **Bayesian A/B testing**: gives direct posterior probabilities and credible intervals, often easier to interpret.  
- Both approaches can lead to similar conclusions, but differ in philosophy and interpretation.  
