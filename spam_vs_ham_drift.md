# 🧪 Spam vs. Ham Drift in AI Classifiers

This page documents two experiments exploring how subtle shifts in training data affect an AI classifier’s reliability. These are practical demonstrations of **model drift** in cybersecurity applications — such as spam filters and threat detectors.

---

## 🧠 Experiment Overview

**Model Used:** Multinomial Naive Bayes (text classifier)  
**Tools:** Python (scikit-learn, matplotlib), Jupyter on Ubuntu VM  
**Dataset:**
- 150 ham (non-spam) emails
- 150 spam emails
- 9 **poisoned ham** emails: written like spam but labeled as ham

---

## 🚨 Experiment 1: Spam Drift

### 🧪 Goal
Simulate a model forgetting what *ham* looks like by feeding it increasingly spam-heavy training sets.

### ⚙️ Method
- Each retrain cycle increases spam ratio
- Ham messages are reduced
- Accuracy tracked after each retrain

### 📉 Results
- Drift begins around **Cycle 5**
- Legitimate messages are flagged as spam

**Real-World Risk:** User emails and business comms are blocked or flagged

---

## 🛑 Experiment 2: Ham Drift

### 🧪 Goal
Simulate a model that forgets what *spam* looks like by overtraining on ham.

### ⚙️ Method
- Spam ratio reduced with each cycle
- Ham dominates the retraining process

### 📉 Results
- Poisoned ham is accepted as legitimate
- Real spam slips through as **false negatives** by **Cycle 4–6**

**Real-World Risk:** Spam/phishing bypasses security filters

---

## 📊 Visual Output
- Accuracy plotted against spam ratio (or ham ratio)
- Red/purple drift lines mark detection threshold crossing
- Console output shows misclassifications across cycles

Example:
```
Cycle 5: Ham = HAM | Poisoned = HAM | Spam = HAM  ← 🚨
```

---

## 🔐 Cybersecurity Implications

| Threat Vector        | AI Impact                        |
|----------------------|----------------------------------|
| Poisoned data        | Trust decay, silent misfires     |
| Overbalanced learning| Concept drift, false classifications |
| Feedback loops       | Model blind spots                |

Defensive AI systems must continuously validate against known-good sets, not just rely on feedback alone.

---

## 🧰 Files & Repo Structure (Suggestion)

```bash
📁 /notebooks/
   ├── spam_drift.ipynb
   ├── ham_drift.ipynb
📄 README.md
📊 drift_comparison.png
🧪 poisoned_examples.txt
```

---

## ✅ Lessons Learned

- Even slight data imbalance can distort classifier behavior
- Monitoring **accuracy trends** alone isn’t enough — inspect predictions
- Implement **drift detection triggers** (accuracy drop %, prediction shift)
- Design datasets to include adversarial edge cases

---

## 📍 Next Ideas
- 🔁 Auto-correct drift by rebalancing data on threshold trip
- 👾 Add more adversarial input types (e.g., obfuscated spam)
- 🔍 Measure vocabulary overlap between cycles
- 🧪 Try with different models: logistic regression, transformers

---

## 👨‍💻 Author
Built by **Enrique Becwar** as part of a CYBR 515 exploration into adversarial machine learning.  
Co-developed with GPT-4o.

🔗 [LinkedIn](https://www.linkedin.com/in/enrique-becwar) | 🛡️ [MaligNet Labs](https://github.com/your-github)

---

*This README can be used as a GitHub homepage or security research portfolio post.*

