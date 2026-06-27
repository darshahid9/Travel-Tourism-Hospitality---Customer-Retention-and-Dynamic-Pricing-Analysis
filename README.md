# Travel-Tourism-Hospitality---Customer-Retention-and-Dynamic-Pricing-Analysis

📌 Problem Statement

In the competitive travel and hospitality sector, hotels lose significant revenue due to:


Unpredictable booking cancellations
Unoptimized room pricing across seasons
No visibility into high-risk customer segments


This project builds the data foundation for a dynamic pricing engine and targeted retention campaigns.


📊 Dataset

PropertyDetailSourceHotel Booking Demand — KaggleRaw Rows119,390Clean Rows86,639Columns32Period2015 – 2017HotelsCity Hotel & Resort Hotel


🗂 Project Structure

hotel-booking-analysis/
│
├── data/
│   ├── hotel_bookings.csv             ← raw dataset (download from Kaggle)
│   ├── hotel_bookings_clean.csv       ← output of Week 1
│   └── customer_segments.csv          ← output of Week 3
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb         ← Week 1
│   ├── 02_eda_analysis.ipynb          ← Week 2
│   ├── 03_churn_prediction.ipynb      ← Week 3
│   ├── 04_customer_segmentation.ipynb ← Week 3
│   └── 05_pricing_dashboard.ipynb     ← Week 4
│
├── src/
│   ├── data_preprocessing.py          ← cleaning functions
│   └── feature_engineering.py         ← feature creation functions
│
├── reports/
│   └── figures/
│       ├── week2_eda/                 ← 14 EDA charts
│       └── week3_models/              ← ROC curve, confusion matrix, clusters
│
├── requirements.txt
├── .gitignore
└── README.md


🔄 Project Pipeline

Raw Data (119K rows)
      ↓
Week 1 — Data Cleaning & Feature Engineering
      ↓
Week 2 — Exploratory Data Analysis (14 charts)
      ↓
Week 3 — Churn Prediction + Customer Segmentation
      ↓
Week 4 — Pricing Dashboard + Business Report


⚙️ Week-by-Week Breakdown

Week 1 — Data Cleaning (01_data_cleaning.ipynb)


Removed 31,994 duplicate rows
Fixed nulls — agent, company → 0 · country → mode · children → 0
Winsorized ADR outliers using IQR (capped at €226.88)
Removed 166 invalid zero-guest bookings
Engineered 8 new features:


FeatureDescriptiontotal_nightsweekend + weekday nightstotal_guestsadults + children + babiestotal_revenueADR × total nightsseasonSpring / Summer / Autumn / Winterlead_time_bucket6 booking window categoriestraveler_typeCorporate vs Leisurehas_special_requestsbinary flagincludes_weekendbinary flag


Week 2 — EDA (02_eda_analysis.ipynb)


14 charts covering cancellation patterns, ADR distribution, booking curve, seasonal trends
Correlation matrix identifying top cancellation drivers
Key findings:

Overall cancellation rate → 27.7%
City Hotel cancels more → 30.2% vs Resort Hotel 23.7%
Peak booking months → July & August
Top cancellation driver → lead_time (highest correlation)
Online TA channel → highest cancellations (18,230)






Week 3 — Churn Prediction (03_churn_prediction.ipynb)


18 features used for modeling
80/20 Train/Test split with stratification


ModelAccuracyROC-AUCLogistic Regression~79%0.84Decision Tree~82%0.87


Top predictors → deposit_type, lead_time, previous_cancellations
Charts → ROC curve, Confusion matrix, Feature importance


Week 3 — Customer Segmentation (04_customer_segmentation.ipynb)


K-Means clustering with StandardScaler + Elbow Method
4 customer segments identified:


ClusterLabel0Budget Short-Stay1Premium Long-Stay2Last-Minute Leisure3Early Planner Corporate


PCA used for 2D cluster visualization



Week 4 — Pricing Dashboard (05_pricing_dashboard.ipynb)


7 interactive Plotly charts
Monthly ADR trend · Weekly demand curve · Revenue heatmap · Segment scatter
Power BI dashboard → 4 pages with full navigation



📈 Power BI Dashboard

PageContent1 — Cancellation & RetentionKPIs, cancellation by segment/deposit/hotel/customer type2 — Seasonal PricingADR trend, monthly bookings, revenue by season3 — Customer SegmentationCorporate vs Leisure, top countries, market segments4 — Lead Time AnalysisBooking curve, cancellation risk by lead time bucket


💡 Key Business Insights

FindingRecommendation27.7% cancellation rateImmediate retention strategy neededLead time > 90 days → 30%+ cancellationRequire deposits for long lead-time bookingsOnline TA = 18,230 cancellationsStricter OTA cancellation policySpecial requests → low cancellationTarget these guests for loyalty programSummer ADR peaks at €205Increase prices 15–20% in July–AugustDirect bookings → lowest cancellationInvest in direct booking campaigns


🚀 How to Run

bash# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/hotel-booking-analysis.git
cd hotel-booking-analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download dataset from Kaggle and place at:
#    data/hotel_bookings.csv

# 4. Run notebooks in order
jupyter notebook
# 01 → 02 → 03 → 04 → 05


🛠 Tech Stack

CategoryToolsData ProcessingPython, Pandas, NumPyVisualizationMatplotlib, Seaborn, PlotlyMachine LearningScikit-LearnDashboardPower BIEnvironmentJupyter Notebook


📁 Requirements

pandas==2.2.2
numpy==1.26.4
matplotlib==3.8.4
seaborn==0.13.2
plotly==5.22.0
scikit-learn==1.4.2
imbalanced-learn==0.12.2
jupyter==1.0.0
scipy==1.13.0



📄 License

This project is for educational and portfolio purposes.
Dataset credit: Antonio, Almeida & Nunes (2019) — Data in Brief
