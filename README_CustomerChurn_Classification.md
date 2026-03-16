# 📉 Customer Churn Classification — Decision Trees & Random Forest

**Course:** MBA Business Data Analytics — A02  
**Tools:** R · rpart · partykit · randomForest · caret · ggplot2  
**Dataset:** Telecom customer churn (liver package) — 20 behavioral/account features

---

## Business Problem

Which customers are likely to leave for a competitor? Predicting churn accurately allows a telecom company to intervene proactively — saving customer relationships before they're lost.

---

## What I Did

**1. Data Preparation**  
- Loaded churn dataset, removed non-predictive identifiers (state, area code, account length)
- Converted `churn` to factor; 70/30 train/test split with `set.seed(1234)`

**2. Classical Decision Tree (rpart)**  
- Built tree using information gain criterion
- Generated CP table, plotted cross-validation error
- Pruned to optimal CP value minimizing `xerror`
- Visualized with `fancyRpartPlot()`

**3. Conditional Inference Tree (partykit)**  
- Built `ctree()` — uses statistical significance tests for splitting, not impurity measures
- Compared confusion matrices: conditional tree outperformed classical tree on churn detection

**4. Random Forest**  
- Trained 500-tree forest (`ntree = 500`, `mtry = √p`)
- Plotted error convergence curve
- Extracted variable importance via `varImpPlot()`

---

## Model Comparison

| Model | Strength | Weakness |
|---|---|---|
| Classical Decision Tree | Interpretable, visual | Missed more churners |
| Conditional Inference Tree | Better statistical rigor | More complex output |
| **Random Forest** ✅ | **Best accuracy, most churners caught** | Less interpretable |

**Most important predictor:** Customer service calls — frequent contacts signal dissatisfaction before cancellation.  
**Least important:** Phone number (identifier, no predictive value).

---

## Business Insight

Unlike medical diagnostics where false negatives (missing a sick patient) are dangerous, churn false negatives mean **losing a customer silently**. The Random Forest minimizes this by catching more churners at the cost of some false alarms — a worthwhile tradeoff for proactive retention.

---

## Files

| File | Description |
|---|---|
| `moralesb-A02.Rmd` | Full classification analysis — all three models |

---

## Skills Demonstrated

`rpart` · `ctree` · `randomForest` · Confusion matrix · Variable importance · CP pruning · 70/30 train-test split · Accuracy calculation · Factor encoding · `fancyRpartPlot`
