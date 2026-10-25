# Applied-Statistics-Project
Three Applied Statistics projects comparing classical and Bayesian methods: hierarchical Bernoulli models, Bayesian regression with MCMC diagnostics, and survival analysis with lifelines.

# Applied Statistics – Course Projects

Three Google Colab notebooks from the **Applied Statistics** course (B.Sc. Statistics & Data Science, 3rd year).
Each notebook takes a real dataset and solves the same problem two ways: with **classical (frequentist) statistics** and with **Bayesian / modern methods**. It then compares the results and discusses when each approach fits.

Every section ends with a short *Lecture question → Answer* block that explains the theory behind the code and points out the method's weaknesses.

---

## Projects

### 1. Bayesian Bernoulli & Hierarchical Models: Titanic survival
**Notebook:** [`COLAB_1_PyMC_Bernoulli_Hierarchical.ipynb`](COLAB_1_PyMC_Bernoulli_Hierarchical.ipynb)

Estimates the probability of survival on the Titanic, overall and by passenger class.

- **Classical:** point estimate $\hat p$, Wald and bootstrap confidence intervals, a binomial test, and χ² and Fisher exact tests for differences between classes.
- **Bayesian (PyMC):** a Beta–Bernoulli model, HDI credible intervals, and a Savage–Dickey Bayes factor.
- **Groups:** separate survival probabilities for each class compared with a **hierarchical model** that shrinks them toward a shared mean, plus pairwise posterior contrasts between classes.
- **Model comparison:** WAIC / LOO with ArviZ, the effective number of parameters, and why BIC is not the right tool here.

### 2. Bayesian Regression & MCMC Diagnostics: Palmer Penguins
**Notebook:** [`COLAB_2_PyMC_Regression_MCMC.ipynb`](COLAB_2_PyMC_Regression_MCMC.ipynb)

Linear regression on the Palmer Penguins dataset, comparing OLS with Bayesian regression.

- **Classical:** `statsmodels` OLS, confidence vs. prediction intervals, one-hot encoding, multicollinearity, VIF, and the dummy-variable trap.
- **Bayesian (PyMC):** a pooled regression with HDI and posterior predictive intervals, and a **hierarchical regression** with a separate intercept for each species (partial pooling).
- **MCMC diagnostics:** $\hat R$, effective sample size, rank plots, autocorrelation, divergences, the "funnel" geometry, and the non-centered parameterization.
- **Insight:** the pooled slope partly reflects the mix of species, a real-data example of Simpson's paradox.

### 3. Survival Analysis with lifelines: Rossi recidivism data
**Notebook:** [`COLAB_3_Lifelines_Survival.ipynb`](COLAB_3_Lifelines_Survival.ipynb)

Analyzes time to re-arrest for released prisoners (Rossi dataset), with a focus on handling censoring correctly.

- **Parametric fits:** exponential vs. Weibull, why fitting on events only is biased under censoring, and a proper censored `WeibullFitter`.
- **Non-parametric:** a naive ECDF vs. the **Kaplan–Meier** survival curve (with the log(−log) CI transform), the **Nelson–Aalen** cumulative hazard, and KM curves comparing prisoners with and without financial aid.
- **Cox proportional hazards:** `CoxPHFitter` with all covariates, partial-effect plots, and a check of the proportional-hazards assumption using scaled Schoenfeld residuals.
- **Discussion:** what to do when proportional hazards fails (stratification, time interactions, the Aalen additive model, AFT models), and lifelines vs. scikit-survival.

---

## Tools & Libraries

| Area | Libraries |
|---|---|
| Bayesian modeling | PyMC, ArviZ |
| Classical statistics | statsmodels, SciPy |
| Survival analysis | lifelines |
| Data & plotting | NumPy, pandas, Matplotlib |

## How to Run

The notebooks were written for **Google Colab** and are saved with their outputs, so you can read them directly on GitHub.

To run them yourself:
1. Open a notebook in [Google Colab](https://colab.research.google.com/) (File → Open notebook → GitHub, then paste this repository's URL).
2. Run all cells. Install any missing package first, for example:
   ```python
   !pip install pymc arviz lifelines
   ```

They also run locally in Jupyter once the libraries above are installed.

## Repository Structure

```
├── COLAB_1_PyMC_Bernoulli_Hierarchical.ipynb   # Titanic – Bernoulli & hierarchical Bayesian models
├── COLAB_2_PyMC_Regression_MCMC.ipynb          # Penguins – OLS vs Bayesian regression, MCMC diagnostics
├── COLAB_3_Lifelines_Survival.ipynb            # Rossi – Kaplan–Meier, Nelson–Aalen, Cox PH
└── README.md
```
