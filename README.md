# Customer Segmentation Using K-Means Clustering

An end-to-end unsupervised machine learning project that applies K-Means clustering to segment customers based on their demographics and purchasing behaviour.

## Project Overview
This project analyses a retail customer dataset with 2,240 records and 29 features and groups customers into 4 distinct segments using K-Means clustering.

### Key Steps
- Data Loading and Exploration
- Preprocessing (missing value imputation, outlier handling, standardisation)
- Optimal K Selection (Elbow Method, Silhouette Score, Davies-Bouldin Index)
- K-Means Clustering with k=4
- PCA Visualisation of clusters
- Cluster Profiling and business interpretation

## Repository Structure
notebooks/customer_segmentation_kmeans.ipynb - Main analysis notebook
data/ - Place your dataset here (not tracked by git)
requirements.txt - Python dependencies
LICENSE - MIT License

## Dataset
Source: https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis

Download customer_segmentation.csv and place it in the data/ folder.

Then update the file path in the notebook:
df = pd.read_csv('../data/customer_segmentation.csv')

## Installation
1. Clone the repository
   git clone https://github.com/jadliudit/customer-segmentation-kmeans.git

2. Install dependencies
   pip install -r requirements.txt

3. Launch Jupyter
   jupyter notebook notebooks/customer_segmentation_kmeans.ipynb

## Tech Stack
- Python, pandas, numpy
- scikit-learn (KMeans, PCA, StandardScaler)
- matplotlib, seaborn, plotly
- Jupyter Notebook

## Author
Udit Jadli
Master of IT (Data Analytics) - Griffith University
