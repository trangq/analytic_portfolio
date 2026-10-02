<div align="center">

# 💳 Credit Card Analytics & ML Portfolio

**Data science across the retail-banking credit card lifecycle — acquire, segment, retain, protect**

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-02A74B)
![XGBoost](https://img.shields.io/badge/XGBoost-EC6B23)
![Prophet](https://img.shields.io/badge/Prophet-Forecasting-0A66C2)
![SQL](https://img.shields.io/badge/SQL-PL%2FSQL-336791)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)

[🇻🇳 Tiếng Việt](README.vi.md)

</div>

> ⚠️ Results are from internal project reviews. No customer data, IDs or proprietary code are included.

---

## 🏆 Featured Projects

| # | Project | Approach | Headline result |
|:-:|---|---|---|
| 1 | 🎯 **Propensity to open a credit card** | LightGBM on ~150–220 behavioral features | **AUC 0.95 · KS 0.76 · 8.49x top-decile lift** |
| 2 | 🎨 **RFM card-user segmentation** | RFM rules + PL/SQL pipeline + Power BI | **6 segments · daily refresh · weekly business use** |
| 3 | 🔁 **Credit card churn model re-tune** | Fresh data + spending / RTC features | **Top lift +10% · AUC ≈ 0.73 (stable)** |
| 4 | 🛡️ **Facebook-ads abuse detection** | Graph analytics + XGBoost | **AUC 0.94** |

---

### 🎯 1. Propensity to Open a Credit Card
Predicts which of ~6M retail customers will open a card in the next **3 months**, so marketing budget goes to the right people.

- **Features:** Casa/term deposit (121), debit card (36), loan (34), demographic (18), snapshotted at 30/09/2024.
- **Model:** LightGBM, chosen after comparing SVM, Logistic Regression, Neural Nets, Random Forest, XGBoost, CatBoost.
- **Result (31/10/2024):** the top 10% of scored customers captured **85%** of all card openers, **8.49x** better than random.
- **Delivery:** ranked Top-N list on request, with an **A/B test** design to measure conversion against the business's usual targeting.

### 🎨 2. RFM Card-User Segmentation
Replaced three requested prediction models (activate / frequency / ticket size) with one transparent segmentation, because all three shared the same goal — **drive spending** — and ML would add training and operating cost with near-identical treatments.

| Segment | RFM rule | Action |
|---|:-:|---|
| 👑 VIP | R4-5 · F4-5 · M4-5 | Premium offers, cashback, limit upgrade |
| 💙 Loyal | R3-5 · F3-5 · M2-5 | Points, rewards, fee waiver |
| 🌱 Potential Loyalist | R4-5 · F3-5 · M3-5 | Spending vouchers |
| ⚠️ Churn Risk | R1-2 · F3-5 · M3-5 | SMS/email reminders, cashback |
| 💤 Churn (Lost) | R1 · F1-2 · M1-2 | Win-back survey, gifts |
| 🆕 New | no transaction yet | First-transaction campaign |

**Engineering:** 7-step PL/SQL package on a daily job → Power BI dashboard, plus a fraud rule to exclude suspicious cardholders.

### 🔁 3. Credit Card Churn Model Re-tune
- Reviewed a 2-year-old model used for SMS targeting; refreshed data and added **spending, hard-rock and request-to-close** features.
- **Top lift 2.7–2.9 → 2.9–3.2 (≈ +10%)**, AUC stable at ≈ 0.73.
- Follow-up impact study showed the rule *"spending dropped 30–50%"* is a weak churn signal, so the recommendation became: **target the highest churn scores, sized by budget.**

### 🛡️ 4. Facebook-Ads Abuse Detection
- Detects customers who repeatedly request refunds on Facebook-ad spend.
- **Graph analytics** exposed relationships between abusers; **XGBoost** used graph, behavioral, spending and demographic features.
- **AUC 0.94**; top features: 12M average CASA balance, number of cards, total suspicious flags, mean ad amount, mean transaction count.

---

## 📈 More Work
EDA on TOI, request-to-close profiles and offer recommendation · spending prediction (customer-level regression, portfolio-level Prophet) · MCC recommender (item-based CF, hit ratio 0.46) · IDC card-closure model (H2O Stacked Ensemble, AUC 0.80) · card-on-file prediction (XGBoost, AUC ≈ 0.9).
See the [full README](README.md) for details.

## 🧰 Tech Stack
Python · R · SQL / PL-SQL · LightGBM · XGBoost · H2O AutoML · Prophet · Collaborative Filtering · Graph analytics · Power BI

## 📬 Contact
**Trang** — Data Scientist · 🔗 [LinkedIn](#) · 📧 [Email](#)
