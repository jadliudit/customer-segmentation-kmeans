# 🛍️ Customer Segmentation with K-Means Clustering: A Comparative Analysis Using Python and R

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![R](https://img.shields.io/badge/R-4.0%2B-276DC3?logo=r&logoColor=white)](https://www.r-project.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0%2B-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen)]()

---

## 📋 Table of Contents

- [Project Description](#-project-description)
- [Dataset Information](#-dataset-information)
- [Methodology](#-methodology)
- [Key Features](#-key-features)
- [Results and Insights](#-results-and-insights)
- [Technologies Used](#-technologies-used)
- [Installation Instructions](#-installation-instructions)
- [How to Run](#-how-to-run)
- [Project Structure](#-project-structure)
- [Visualizations](#-visualizations)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 📌 Project Description

This project implements **K-Means clustering** for customer segmentation and performs a **cross-platform comparative analysis** between Python and R. The goal is to group customers into meaningful segments based on their demographic information, purchasing behaviour, and marketing campaign responses — enabling businesses to design targeted marketing strategies, personalise product recommendations, and improve customer engagement.

The project addresses a core business problem: *how can an organisation systematically identify distinct customer groups to drive smarter, data-led decisions?* By clustering customers on features such as income, product expenditure, and recency of purchase, this analysis provides actionable insights into four well-defined customer segments.

A secondary objective is to evaluate and compare how Python (`scikit-learn`) and R (`cluster`, `factoextra`) handle the same clustering task — examining differences in inertia, Silhouette Score, and Davies-Bouldin Index across both platforms.

---

## 📊 Dataset Information

| Property | Details |
|---|---|
| **Source** | [Kaggle — Customer Segmentation Dataset](https://www.kaggle.com/datasets/vishakhdapat/customer-segmentation-clustering) |
| **Records** | 2,240 customers |
| **Features** | 29 variables (demographics, spending, campaign responses) |
| **Target** | Unsupervised — no pre-defined labels |

### Key Features in the Dataset

| Category | Variables |
|---|---|
| **Demographics** | `Year_Birth`, `Education`, `Marital_Status`, `Income` |
| **Household** | `Kidhome`, `Teenhome` |
| **Spending** | `MntWines`, `MntFruits`, `MntMeatProducts`, `MntFishProducts`, `MntSweetProducts`, `MntGoldProds` |
| **Purchases** | `NumDealsPurchases`, `NumWebPurchases`, `NumCatalogPurchases`, `NumStorePurchases` |
| **Engagement** | `NumWebVisitsMonth`, `Recency` |
| **Campaigns** | `AcceptedCmp1` – `AcceptedCmp5`, `Response` |

### Preprocessing Steps Applied

1. **Missing Value Handling** — 24 missing values in `Income` were imputed using the median (Python) and mean (R)
2. **Outlier Treatment** — IQR-based capping applied to all numerical columns (Python)
3. **Feature Engineering** — `Enrolment_Age` derived from `Dt_Customer` and `Year_Birth`
4. **Feature Removal** — `ID`, `Z_CostContact`, and `Z_Revenue` dropped (non-informative)
5. **Standardisation** — `StandardScaler` (Python) and `scale()` (R) applied to normalise all numeric features

---

## 🔬 Methodology

The project follows a structured machine learning pipeline:

```
Raw Data → Preprocessing → Optimal k Selection → K-Means Clustering → PCA Visualisation → Cluster Analysis
```

### 1. Optimal Cluster Selection
Three complementary metrics were used to determine the ideal number of clusters:

- **Elbow Method** — Plots Within-Cluster Sum of Squares (WSS/Inertia) against k; the "elbow" point indicates diminishing returns
- **Silhouette Score** — Measures how well-separated clusters are (higher = better)
- **Davies-Bouldin Index** — Measures cluster compactness and separation (lower = better)

Although all three metrics suggested **k=2** as statistically optimal, **k=4** was selected to achieve greater granularity and more actionable business insights.

### 2. K-Means Clustering
- Algorithm: K-Means with `k-means++` initialisation
- Multiple restarts: `nstart = 10` for stability
- Fixed random seed for reproducibility
- Applied identically in both Python (`scikit-learn`) and R (`cluster` package)

### 3. Dimensionality Reduction
- **Principal Component Analysis (PCA)** used to project high-dimensional cluster results into 2D for visualisation

---

## ✨ Key Features

- ✅ End-to-end customer segmentation pipeline in both Python and R
- ✅ Cross-platform comparison of K-Means clustering results
- ✅ Three evaluation metrics: Elbow Method, Silhouette Score, Davies-Bouldin Index
- ✅ PCA-based 2D cluster visualisation with centroids and connecting lines
- ✅ Cluster-wise analysis of income, spending, recency, household composition, and campaign responsiveness
- ✅ Well-commented, beginner-friendly code with clear inline documentation
- ✅ Side-by-side Python vs R metric comparison plots

---

## 📈 Results and Insights

Both Python and R converged on **k=4** as the chosen number of clusters. The performance metrics at k=4 were:

| Metric | Python (k=4) | R (k=4) |
|---|---|---|
| **Elbow Method (Inertia/WSS)** | 34,262.87 | 34,004.24 |
| **Silhouette Score** | 0.1880 | 0.1930 |
| **Davies-Bouldin Index** | 2.0255 | 2.2117 |

### Customer Segment Profiles (Python)

| Cluster | Income | Key Behaviour | Marketing Strategy |
|---|---|---|---|
| **Cluster 0** — Budget Families | ~$33,660 | Low spenders, high web visits, more children at home | Web-based deals, family-friendly promotions |
| **Cluster 1** — Affluent In-Store Shoppers | ~$70,516 | High wine & meat spend, prefer in-store, moderate campaign response | Premium loyalty programs, in-store incentives |
| **Cluster 2** — Health-Conscious Mid-Income | ~$55,430 | Moderate spend, older demographic (~50 yrs), fruit preference | Health & wellness campaigns, omnichannel offers |
| **Cluster 3** — High-Value Loyalists | ~$81,287 | Highest spend on wine & meat, highly campaign-responsive | Exclusive premium campaigns, in-store loyalty rewards |

### Key Comparative Findings

- **R produced more compact clusters** — lower inertia values than Python
- **R achieved higher Silhouette Score** — slightly better cluster separation
- **Python achieved lower Davies-Bouldin Index** — indicating stronger cluster compactness
- A notable surprise: Cluster 3 was characterised differently between platforms due to differences in centroid initialisation and numerical precision — highlighting the importance of cross-platform validation

---

## 🛠️ Technologies Used

### Python Stack
| Tool | Version | Purpose |
|---|---|---|
| Python | 3.8+ | Core language |
| pandas | 1.3+ | Data manipulation |
| NumPy | 1.21+ | Numerical operations |
| scikit-learn | 1.0+ | K-Means clustering, PCA, evaluation metrics |
| Matplotlib | 3.4+ | Plotting |
| Seaborn | 0.11+ | Statistical visualisation |
| Plotly | 5.0+ | Interactive charts |
| Jupyter Notebook | — | Development environment |

### R Stack
| Tool | Version | Purpose |
|---|---|---|
| R | 4.0+ | Core language |
| cluster | — | K-Means clustering |
| factoextra | — | Clustering visualisation, Elbow/Silhouette plots |
| ggplot2 | — | High-quality cluster visualisations |
| clusterSim | — | Davies-Bouldin Index |
| dplyr / tidyr | — | Data manipulation |
| RStudio | — | Development environment |

---

## ⚙️ Installation Instructions

### Prerequisites
- Python 3.8 or higher
- R 4.0 or higher (optional, for R analysis)
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/uditjadli/covid19-global-analysis.git
cd customer-segmentation
```

> **Note:** Replace the URL above with your actual repository URL once published.

### 2. Set Up Python Environment

```bash
# Create a virtual environment
python -m venv venv

# Activate the environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 3. Install R Packages (Optional)

Open RStudio or an R console and run:

```r
install.packages(c("dplyr", "ggplot2", "cluster", "factoextra", "clusterSim", "tidyr"))
```

### 4. Download the Dataset

Download the dataset from [Kaggle](https://www.kaggle.com/datasets/vishakhdapat/customer-segmentation-clustering) and place the file `Customer_Segmentation_Kaggle.csv` in the `data/` directory.

---

## ▶️ How to Run

### Python Analysis

```bash
# Activate your virtual environment first, then:
jupyter notebook notebooks/customer_segmentation_python.ipynb
```

Run all cells in order. The notebook is structured as follows:
1. Data loading and exploration
2. Preprocessing (missing values, outliers, standardisation)
3. Optimal k determination (Elbow, Silhouette, Davies-Bouldin)
4. K-Means clustering with k=4
5. PCA visualisation
6. Cluster-wise analysis
7. Python vs R comparison plots

### R Analysis

Open `notebooks/customer_segmentation_r.Rmd` in RStudio and click **Knit**, or run the script directly:

```r
source("scripts/customer_segmentation.R")
```

### Running Both (for comparison)

Run the Python notebook first to generate comparison data, then run the R script. The comparison plots in Section 9 of the Python notebook use hardcoded values from both platforms.

---

## 📁 Project Structure

```
customer-segmentation/
│
├── data/
│   └── Customer_Segmentation_Kaggle.csv        # Raw dataset (download from Kaggle)
│
├── notebooks/
│   ├── customer_segmentation_python.ipynb      # Full Python analysis (Jupyter)
│   └── customer_segmentation_r.Rmd             # Full R analysis (R Markdown)
│
├── scripts/
│   └── customer_segmentation.R                 # Standalone R script
│
├── outputs/
│   ├── cluster_analysis.csv                    # Cluster mean characteristics
│   └── figures/                                # All generated plots (PNG)
│       ├── elbow_method_python.png
│       ├── elbow_method_r.png
│       ├── silhouette_comparison.png
│       ├── dbi_comparison.png
│       ├── pca_clusters_python.png
│       ├── pca_clusters_r.png
│       ├── cluster_centroids.png
│       ├── income_expenditure_bars.png
│       ├── kidhome_teenhome_lollipop.png
│       ├── recency_boxplot.png
│       ├── deals_violin.png
│       ├── web_store_purchases.png
│       └── marketing_responses_stacked.png
│
├── requirements.txt                            # Python dependencies
├── README.md                                   # Project documentation
└── LICENSE                                     # MIT License
```

---

## 📉 Visualizations

The project generates the following charts and plots:

| Visualisation | Type | Purpose |
|---|---|---|
| Elbow Method (Python & R) | Line plot | Determine optimal k via inertia |
| Silhouette Score Comparison | Line plot | Compare cluster quality across platforms |
| Davies-Bouldin Index Comparison | Line plot | Compare cluster compactness across platforms |
| PCA Cluster Plot | 2D Scatter | Visualise cluster separation in reduced dimensions |
| Cluster Centroids Plot | Scatter + lines | Show centroid positions and point distances |
| Mean Income per Cluster | Bar chart | Income distribution across segments |
| Mean Wine/Meat/Fruit Expenditure | Bar charts | Spending profile per segment |
| Children & Teens in Household | Lollipop charts | Family composition per segment |
| Recency Distribution | Box plot | Purchase recency by segment |
| Deals Purchased | Violin plot | Promotional engagement by segment |
| Web vs Store Purchases | Side-by-side bar | Channel preference by segment |
| Marketing Campaign Responses | Stacked bar | Campaign acceptance rates by segment |
| Boxplot (Before/After Outlier Treatment) | Box plot | Data quality validation |
| Boxplot (Before/After Standardisation) | Box plot | Feature scaling validation |

---

## 🤝 Contributing

Contributions are welcome! Here's how to get involved:

1. **Fork** the repository
2. **Create** a new feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with a clear message:
   ```bash
   git commit -m "Add: description of your change"
   ```
4. **Push** to your branch:
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open** a Pull Request with a clear description of what you've changed and why

### Contribution Ideas
- Add alternative clustering algorithms (DBSCAN, Hierarchical, Gaussian Mixture)
- Extend the R analysis with additional visualisations
- Implement an interactive Plotly/Dash dashboard for cluster exploration
- Add RFM (Recency, Frequency, Monetary) analysis as a complementary method
- Include automated hyperparameter tuning for k selection

Please ensure your code follows existing formatting conventions and is well-commented.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 Udit Jadli

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 👤 Author

**Udit Jadli**

- 🎓 Master of Information Technology (Data Analytics) — Griffith University *(Academic Excellence Award)*
- 🎓 Master of Science (Mathematics)
- 📍 Brisbane, Australia

| Platform | Link |
|---|---|
| **GitHub** | [github.com/uditjadli](https://github.com/uditjadli) |
| **LinkedIn** | [linkedin.com/in/uditjadli](https://linkedin.com/in/uditjadli) |
| **Email** | Available on request |

---

*This project was completed as part of the 7021ICT – Applied Data Mining course at Griffith University (2024).*
