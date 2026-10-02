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


<div align="center">

# 💳 Portfolio Phân tích & Machine Learning Thẻ Tín Dụng

**Data science xuyên suốt vòng đời khách hàng ngân hàng bán lẻ — từ thu hút, phân khúc, giữ chân, thúc đẩy chi tiêu đến phát hiện gian lận**

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-02A74B)
![XGBoost](https://img.shields.io/badge/XGBoost-EC6B23)
![H2O AutoML](https://img.shields.io/badge/H2O-AutoML-FFC500)
![Prophet](https://img.shields.io/badge/Prophet-Forecasting-0A66C2)
![SQL](https://img.shields.io/badge/SQL-PL%2FSQL-336791)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)
![R](https://img.shields.io/badge/R-EDA-276DC3?logo=r&logoColor=white)

[🇬🇧 English](README.md) · 🇻🇳 **Tiếng Việt**

</div>

---

## 📌 Tổng quan

Repo này tóm tắt các dự án phân tích và machine learning xoay quanh mảng **thẻ tín dụng (CC)** của một ngân hàng bán lẻ, bao phủ toàn bộ vòng đời khách hàng:

```
 Thu hút ──▶ Kích hoạt ──▶ Tăng chi tiêu ──▶ Giữ chân ──▶ Bảo vệ
 Propensity   RFM          Dự báo chi tiêu    Churn /     Gian lận &
 mở thẻ       phân khúc    Gợi ý MCC          RTC offer   lạm dụng quảng cáo
```

> ⚠️ **Lưu ý:** Các số liệu là kết quả báo cáo từ các buổi review dự án nội bộ. Repo **không** chứa dữ liệu khách hàng, mã khách hàng hay source code độc quyền.

## 🏆 Điểm nhấn

| Dự án | Loại bài toán | Thuật toán | Kết quả nổi bật |
|---|---|---|---|
| [Propensity mở thẻ tín dụng](#1-propensity-mở-thẻ-tín-dụng) | Phân loại | LightGBM | **AUC 0.95 · KS 0.76 · Lift top decile 8.49x** |
| [Phân khúc khách hàng RFM](#2-phân-khúc-khách-hàng-dùng-thẻ-rfm) | Phân khúc + Tự động hóa | RFM, SQL package | **6 phân khúc, dashboard Power BI hằng tuần** |
| [Re-tune mô hình churn thẻ](#3-re-tune-mô-hình-churn-thẻ-tín-dụng) | Phân loại | Tree-based | **Top lift tăng 10%, AUC ≈ 0.73 ổn định** |
| [Dự đoán đóng thẻ IDC](#6-dự-đoán-đóng-thẻ-idc) | Phân loại | H2O Stacked Ensemble | **AUC 0.80 · KS 0.46 · Top lift 4.6x** |
| [Dự đoán dùng COF](#7-dự-đoán-khách-hàng-dùng-card-on-file-cof) | Phân loại | XGBoost | **AUC 0.89 – 0.91** |
| [Dự đoán chi tiêu từng khách hàng](#8-dự-đoán-chi-tiêu-thẻ-từng-khách-hàng) | Hồi quy | Gradient boosting | **Pilot T12/2023 trên 19k khách hàng** |
| [Dự báo chi tiêu toàn danh mục](#9-dự-báo-chi-tiêu-toàn-danh-mục) | Time series | Prophet | **MAPE thấp nhất so với SARIMA/ARIMA/regression** |
| [Gợi ý MCC](#10-gợi-ý-mcc) | Recommender | Item-based CF | **Hit ratio 0.46 · Precision@K 0.43 · Recall@K 0.50** |
| [Phát hiện gian lận quảng cáo Facebook](#12-phát-hiện-gian-lận-lạm-dụng-quảng-cáo-facebook) | Phân loại + Graph | XGBoost | **AUC 0.94** |

---

## 🎯 1. Propensity mở thẻ tín dụng

**Mục tiêu:** Dự đoán khách hàng cá nhân có khả năng cao mở thẻ tín dụng trong **3 tháng tới**, giúp tối ưu ngân sách marketing và bán chéo (~6 triệu khách hàng cá nhân).

**Dữ liệu & biến** — ~150–220 biến hành vi và biến phái sinh, tổng hợp tại mốc **30/9/2024**, nhãn quan sát 3 tháng tiếp theo:

| Nhóm biến | Số biến | Ví dụ |
|---|:-:|---|
| Casa / Tiền gửi | 121 | Số dư EOP, trung bình tháng/ngày, max/min, YTD/MTD, kỳ hạn TB, số tài khoản |
| Thẻ debit | 36 | Số loại thẻ, tỷ lệ sử dụng hạn mức, ngày giao dịch gần nhất |
| Khoản vay | 34 | Số khoản vay, hạn mức, kỳ hạn, trạng thái, loại hình tất toán |
| Nhân khẩu học | 18 | Tuổi, giới tính, tình trạng hôn nhân, chi nhánh mở CIF |

**Điều kiện tập dữ liệu:** khách hàng cá nhân · có ≥ 1 giao dịch tài khoản thanh toán trong 3 tháng gần nhất · CIF chưa đóng · chưa từng mở thẻ tín dụng.

**Chọn mô hình:** so sánh SVM, Logistic Regression, Neural Network và các mô hình cây (Decision Tree, Random Forest, XGBoost, CatBoost, **LightGBM**). Các thuật toán boosting luôn cho kết quả cao nhất với bài toán phân loại → chọn **LightGBM**.

**Kết quả (tập test, 31/10/2024)**

| Chỉ số | Giá trị |
|---|:-:|
| AUC | **0.95** |
| KS | **0.76** |
| Positives trong top 10% | **5,492 → 85%** tổng số khách hàng mở thẻ |
| Lift top decile | **8.49x** so với random |

**Triển khai:** Trung tâm phân tích trả danh sách **Top N** (mã khách hàng + điểm propensity) theo yêu cầu; đơn vị kinh doanh có thể chạy **A/B test** (tập mô hình vs. tập truyền thống) để so sánh conversion rate.

---

## 🎨 2. Phân khúc khách hàng dùng thẻ (RFM)

**Vì sao chọn RFM?** Nghiệp vụ ban đầu đề xuất 3 mô hình dự đoán riêng (active thẻ, tăng tần suất, tăng doanh số/thẻ). Phân tích cho thấy cả ba cùng mục đích là **thúc đẩy chi tiêu**, mô hình ML tốn nhiều thời gian training, kiểm định, vận hành mà cách treatment gần như không khác nhau. Vì vậy đề xuất phân khúc **RFM / luật** minh bạch, dễ vận hành.

**Phạm vi:** khách hàng đang dùng thẻ tín dụng và chưa đóng thẻ, chia **6 phân khúc** + **rule fraud** loại khách hàng có hành vi đáng nghi.

| Phân khúc | Mô tả | Điều kiện RFM | Chiến lược tiếp cận |
|---|---|:-:|---|
| 👑 VIP | Chi tiêu cao, thường xuyên, gần đây | R4-5 · F4-5 · M4-5 | Ưu đãi cao cấp, cashback, nâng hạn mức/thẻ |
| 💙 Loyal | Thường xuyên, chi tiêu vừa | R3-5 · F3-5 · M2-5 | Tích điểm, thưởng, miễn phí thường niên |
| 🌱 Potential Loyalist | Mới tiêu, tần suất tốt | R4-5 · F3-5 · M3-5 | Voucher chi tiêu, hoàn tiền thanh toán hóa đơn |
| ⚠️ Churn Risk | Từng tiêu nhiều, lâu không dùng | R1-2 · F3-5 · M3-5 | Email/SMS nhắc nhở, hoàn tiền kích thích giao dịch |
| 💤 Churn (Lost) | Không còn hoặc ít giao dịch | R1 · F1-2 · M1-2 | Khảo sát lý do, giảm phí, quà tặng nếu quay lại |
| 🆕 New | Đã mở thẻ, chưa giao dịch | — | Chiến dịch kích hoạt giao dịch đầu tiên |

**Kỹ thuật:** **PL/SQL package** gồm 7 bước (`STEP1…STEP7`: transactions → monthly → segment → result → final → run) chạy **job hằng ngày**, hiển thị trên **Power BI** (treemap + bảng chi tiết khách hàng), nghiệp vụ tiếp cận theo **tuần**.

---

## 🔁 3. Re-tune mô hình churn thẻ tín dụng

- **Vấn đề:** mô hình churn đã chạy 2 năm, dùng để chọn khách hàng gửi SMS; cần review lại.
- **Giải pháp:** cập nhật dữ liệu mới nhất, bổ sung biến về **trạng thái chi tiêu, hard-rock (không chi tiêu), yêu cầu đóng thẻ (RTC)**.
- **Kết quả:** top lift decile 10 từ **2.7–2.9 → 2.9–3.2**, tăng **≈ 10%**; AUC ổn định **≈ 0.73** trong các tháng gần đây.

## 📏 4. Đo lường hiệu quả mô hình churn

- Kiểm định 4 tháng: **top lift 3.5 – 3.8**.
- Phát hiện rule *"chi tiêu giảm 30–50%"* là **tín hiệu yếu** (khách có thể chỉ giảm vì trước đó chi quá nhiều).
- **Đề xuất:** chọn khách có **churn score cao nhất**, số lượng theo ngân sách marketing.

---

## 🔍 5. Các phân tích khám phá (EDA)

<details>
<summary><b>💰 Phân tích TOI khách hàng thẻ tín dụng</b></summary>

- TOI đạt đỉnh tại **MOB 3 và MOB 13** (cả NFI và NII).
- Chi tiêu càng cao → TOI càng cao.
- Tỷ lệ TOI dương cao nhất: **Titanium Lady, Step Up (~95%)**; tỷ lệ TOI âm cao nhất: **Super Shopee (~36%)**.
- TOI trung bình tháng: AF & MAF ≈ **150k VND**, MASS ≈ **107k VND**.
</details>

<details>
<summary><b>📞 Chân dung khách hàng yêu cầu đóng thẻ (RTC)</b></summary>

- ~50% khách không nêu lý do; lý do phổ biến thứ hai: *không có POS gần, thích dùng tiền mặt*.
- ~80% gọi đóng thẻ **1–2 lần**; lần đầu sau ≈ **7 tháng** mở thẻ, lần hai sau ≈ 3 tháng.
- Tỷ lệ RTC cao nhất: **Super Shopee (30%)**, **Titanium Lady (18%)**.
- ~30% giữ chân thành công không cần offer; ~25% nhận offer miễn phí thường niên.
</details>

<details>
<summary><b>🎁 Gợi ý offer cho khách hàng RTC</b></summary>

- Thay offer *"miễn phí thường niên kỳ tới"* đại trà bằng **offer theo nhóm** (không offer / phí thường niên / cashback), dựa trên MOB, sản phẩm đang sở hữu, revolver, loại thẻ, lịch sử RTC, chi tiêu, TOI.
- Khách thỏa **4/7 đặc điểm** có thể giữ chân **không cần offer**.
- Xây **công cụ Check Offer trên Excel**: nhập số hợp đồng → ra offer 1 và offer 2 đề xuất.
</details>

<details>
<summary><b>🛍️ Phân tích để thúc đẩy chi tiêu thẻ</b></summary>

- Chi tiêu tăng sau **ngày sao kê** và **ngày lương**, vào **quý 4 và dịp Tết**.
- **~70%** khách chi tiêu ngay tháng đầu; tháng 1 và tháng 4 có tỷ lệ dùng thẻ cao nhất.
- **Market & Store** là MCC chi nhiều nhất về số lượng và giá trị ở các dòng thẻ phổ biến.
- Đề xuất: tính năng tổng hợp MCC chi tiêu trên app → bán chéo thẻ Lady/World (5% cashback Market & Store), cashback linh hoạt và cá nhân hóa theo lịch sử giao dịch.
</details>

<details>
<summary><b>📊 So sánh các nhóm chi tiêu</b></summary>

- Phân bổ: **giảm 31.3% · tăng 30% · không chi tiêu 29.7%** · newbie 6.7% · ổn định 2.2%.
- ~100k khách chưa từng giao dịch sau khi mở thẻ (chủ yếu thẻ MC2 / No1).
- Trong nhóm đã churn (thẻ mở sau 01/2022), **50% ngừng chi tiêu 2 tháng liên tiếp**.
- Mọi nhóm chi nhiều nhất ở tháng đầu; nhóm giảm chi tiêu sụt mạnh từ **tháng thứ 2**.
</details>

---

## 🤖 Các mô hình dự đoán

### 6. Dự đoán đóng thẻ IDC
- **Bài toán:** dự đoán thẻ IDC bị đóng trong 3 tháng tới (mức thẻ).
- **Cách làm:** undersampling + stratified sampling (~1% churn); train T11/2022, validate T5, T8, T10/2022.
- **Mô hình:** H2O **Stacked Ensemble** (5 base models: 1 DRF, 3 GBM, 1 GLM).
- **Kết quả:** **AUC 0.80 · KS 0.46 · lift top decile 4.6x** (46% thẻ đóng nằm trong top 10%).
- **Bài học:** train ở mức thẻ cho phân tách tốt hơn; chọn khung thời gian dự đoán phù hợp với nhãn.

### 7. Dự đoán khách hàng dùng Card-on-File (COF)
- **Bài toán:** dự đoán khách lần đầu dùng COF thanh toán online trong tháng tới.
- **Mô hình:** **XGBoost**, train trên 4 snapshot theo quý (~4% positive), validate T3/T4-2023.
- **Kết quả:** **AUC ≈ 0.89 – 0.91**.
- **Biến quan trọng:** tổng giá trị giao dịch online, số thẻ tín dụng, số giao dịch, merchant flag, nhóm tuổi.

### 8. Dự đoán chi tiêu thẻ từng khách hàng
- **Bài toán:** dự báo chi tiêu tháng tới của từng khách để ước tính ngân sách cashback và nhận diện khách giảm chi tiêu.
- **Mô hình:** hồi quy trên **top 50 biến** (thẻ tín dụng, nhân khẩu học, giao dịch, tiền gửi).
- **Đầu ra:** nhóm xu hướng (tăng / giảm / giữ nguyên) + số tiền dự đoán.
- **Pilot (T12/2023):** chọn **19k khách dự đoán giảm chi tiêu**, kết hợp mô hình next-MCC để chọn offer phù hợp.

### 9. Dự báo chi tiêu toàn danh mục
- **Bài toán:** dự báo chi tiêu tháng tới của cả danh mục phục vụ lập ngân sách và kế hoạch theo mùa vụ.
- **So sánh:** Prophet · hồi quy supervised · SARIMA / ARIMA.
- **Chọn:** **Prophet** (MAPE thấp nhất) với seasonality theo năm + tuần, lịch lễ Việt Nam, chế độ multiplicative. Pilot trên dữ liệu T12/2024.

### 10. Gợi ý MCC
- **Bài toán:** gợi ý nhóm ngành hàng (MCC) khách có khả năng chi tiêu tiếp theo.
- **So sánh:** item-based CF · user-based CF · matrix factorization.
- **Kết quả item-based CF:**

| Chỉ số | Giá trị | Ý nghĩa |
|---|:-:|---|
| Hit ratio | 0.461 | 46% khách nhận ≥ 1 gợi ý đúng |
| Precision@K | 0.426 | 42.6% gợi ý trong top K là đúng |
| Recall@K | 0.504 | 50.4% MCC thực chi tiêu được gợi ý trúng |

---

## 🛡️ Phân tích gian lận & lạm dụng

### 11. Chi tiêu IDC cho dịch vụ quảng cáo — hồ sơ hành vi đáng nghi
Hồ sơ rủi ro theo luật, kết hợp giả thuyết nghiệp vụ và insight dữ liệu: chi tiêu quảng cáo cao, mở/đóng nhiều thẻ, nhiều loại thẻ IDC, thẻ mở rồi đóng trong 1 tháng, Casa thấp, nằm trong danh sách chargeback, tỷ lệ giao dịch hủy cao.

### 12. Phát hiện gian lận, lạm dụng quảng cáo Facebook
- **Bài toán:** nhận diện sớm khách hàng liên tục yêu cầu hoàn tiền khoản chi quảng cáo Facebook.
- **Cách làm:** **graph analytics** để tìm quan hệ giữa các khách gian lận + **XGBoost** với biến graph, hành vi đáng nghi, chi tiêu, nhân khẩu học.
- **Kết quả:** **AUC 0.94** trên tập test T9, T10/2023.
- **Biến quan trọng:** số dư Casa bình quân 12 tháng, số thẻ, tổng cờ đáng nghi, giá trị quảng cáo TB, số giao dịch TB.

---

## 🧰 Công nghệ

| Mảng | Công cụ |
|---|---|
| Mô hình | LightGBM · XGBoost · H2O AutoML (Stacked Ensemble) · Prophet · SARIMA/ARIMA · Collaborative Filtering |
| Phân tích | Python · R · SQL |
| Kỹ thuật dữ liệu | PL/SQL package & scheduled job |
| Trực quan | Power BI · công cụ Excel · matplotlib / ggplot2 |
| Kỹ thuật | Lift / Gain / KS / AUC · A/B testing · Graph analytics · RFM · Seasonality |

## 🔑 Bài học rút ra

1. **Đặt đúng bài toán nghiệp vụ quan trọng hơn mô hình phức tạp** — 3 mô hình ML được yêu cầu gộp thành 1 giải pháp RFM minh bạch, triển khai nhanh, dễ vận hành.
2. **Luôn kiểm chứng rule bằng dữ liệu** — rule "chi tiêu giảm 30–50%" nghe hợp lý nhưng là tín hiệu yếu.
3. **Chọn đúng đơn vị và khung thời gian dự đoán** — train ở mức thẻ và đúng horizon giúp tăng độ phân tách.
4. **Đi hết "dặm cuối"** — pipeline tự động, dashboard Power BI, công cụ Excel giúp nghiệp vụ dùng được ngay.

## 📬 Liên hệ

**Trang** — Data Scientist
🔗 [LinkedIn](#) · 📧 [Email](#) · 🌐 [Portfolio](#)

---

<div align="center">
<sub>⭐ Nếu thấy hữu ích, hãy để lại một star cho repo nhé.</sub>
</div>
