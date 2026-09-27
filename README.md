# 🛒 SmartCart — E-commerce Customer Segmentation

SmartCart is a **customer segmentation project using unsupervised machine learning**. The goal of the project is to identify groups of customers with similar purchasing behaviour and characteristics, and then interpret those groups from a business perspective.

The project covers the complete workflow from data preprocessing and feature engineering to clustering, visualization, and customer-segment analysis.

---

## 📌 Project Overview

Understanding different types of customers can help an e-commerce business design more targeted marketing strategies.

In this project, I worked with the **SmartCart customer dataset** and used clustering techniques to discover distinct customer segments based on factors such as:

* Income
* Spending behaviour
* Purchase activity
* Web activity
* Catalog purchases
* Store purchases
* Household characteristics
* Customer tenure
* Demographic information

Two clustering techniques were explored:

* **K-Means Clustering**
* **Agglomerative Hierarchical Clustering**

The resulting clusters were then analyzed to understand their characteristics and possible marketing strategies.

---

## 🔄 Project Workflow

```text
SmartCart Dataset
       ↓
Data Exploration
       ↓
Data Preprocessing
       ↓
Missing Value Handling
       ↓
Feature Engineering
       ↓
Feature Selection
       ↓
Outlier Detection & Handling
       ↓
Correlation Analysis
       ↓
Categorical Encoding
       ↓
Feature Scaling
       ↓
PCA Visualization
       ↓
Choosing Optimal Number of Clusters
       ↓
K-Means & Agglomerative Clustering
       ↓
Cluster Analysis
       ↓
Customer Segmentation
       ↓
Business Insights & Marketing Strategies
```

---

## 📊 Dataset

The project uses customer-level e-commerce data containing demographic, purchasing, and campaign-related information.

Some of the important variables include:

* `Income`
* `Year_Birth`
* `Education`
* `Marital_Status`
* `Kidhome`
* `Teenhome`
* `Dt_Customer`
* `Recency`
* `MntWines`
* `MntFruits`
* `MntMeatProducts`
* `MntFishProducts`
* `MntSweetProducts`
* `MntGoldProds`
* `NumWebPurchases`
* `NumCatalogPurchases`
* `NumStorePurchases`
* `NumWebVisitsMonth`
* `Response`

---

## 🧹 Data Preprocessing

The dataset was explored and cleaned before applying clustering algorithms.

### Missing Values

Missing values in the `Income` feature were handled using the **median**, making the preprocessing less sensitive to extreme income values.

### Feature Engineering

Several new features were created to make the customer information easier to interpret:

**Age**

Derived from `Year_Birth`.

**Customer Tenure**

Calculated from the customer registration date.

**Total Spending**

Combined spending across different product categories:

```text
Total_Spending =
MntWines
+ MntFruits
+ MntMeatProducts
+ MntFishProducts
+ MntSweetProducts
+ MntGoldProds
```

**Total Children**

```text
Total_Children = Kidhome + Teenhome
```

### Feature Simplification

Some categorical variables were simplified to reduce unnecessary category fragmentation.

For example:

* Education categories were grouped into broader education levels.
* Marital status was transformed into a `Living_With` feature representing household status.

Unnecessary and redundant columns were then removed.

---

## 🚨 Outlier Detection

Outliers were explored using visual analysis, including pair plots.

Extreme values in selected features were removed using domain-based thresholds before continuing with clustering.

The cleaned dataset was then used for the remaining analysis.

---

## 🔗 Correlation Analysis

A correlation heatmap was created to understand relationships between numerical features.

This helped identify strongly related variables and provided a better understanding of the underlying customer behaviour before clustering.

---

## 🔤 Encoding & Feature Scaling

Categorical variables were converted into numerical representations using **One-Hot Encoding**.

The resulting features were then standardized using:

```python
StandardScaler()
```

Scaling is particularly important for clustering because both K-Means and Ward-based hierarchical clustering rely on distance calculations.

---

## 📉 PCA Visualization

Principal Component Analysis (PCA) was used to reduce the processed feature space to **three principal components** for visualization.

This allowed the customer data to be visualized in three dimensions and provided a way to observe the distribution of customers in the reduced feature space.

The three selected components captured approximately **44.5% of the variance** in the processed data.

---

## 🔢 Choosing the Number of Clusters

Two approaches were used to determine a suitable number of clusters:

### 1. Elbow Method

The Within-Cluster Sum of Squares (WCSS) was calculated for different values of `K`.

The elbow point indicated **4 clusters** as a suitable choice.

### 2. Silhouette Score

Silhouette scores were calculated for different cluster counts to evaluate how well-separated and cohesive the resulting clusters were.

Together, these methods supported using:

```text
K = 4
```

for the clustering experiments.

---

## 🤖 Clustering Algorithms

### K-Means Clustering

K-Means was applied with four clusters.

The algorithm groups customers by minimizing the distance between customers and their respective cluster centroids.

### Agglomerative Clustering

Hierarchical Agglomerative Clustering was also applied using **Ward linkage**.

The resulting clusters were compared with the K-Means segmentation, and the Agglomerative clustering results were used for the final cluster analysis in the notebook.

---

## 👥 Customer Segments

The final clustering produced **four customer segments**.

The clusters were analyzed using characteristics such as:

* Average income
* Total spending
* Purchase frequency
* Web activity
* Catalog purchases
* Store purchases
* Household characteristics
* Campaign response

The analysis showed distinct groups ranging from lower-spending customers to high-income, high-spending customers.

Rather than treating the cluster numbers themselves as meaningful, the clusters were interpreted based on their underlying customer characteristics.

---

## 💡 Business Insights

The segmentation can be used to think about different marketing approaches for different customer groups.

Examples include:

### Lower-Spending Customers

Potential strategies include:

* Discount-based offers
* Coupons
* Product bundles
* Family-oriented promotions

### High-Value Customers

Potential strategies include:

* Loyalty programs
* Personalized recommendations
* Premium product offers
* Exclusive promotions

### Digitally Active Customers

Customers with higher web activity can potentially be targeted through:

* Personalized online offers
* Digital campaigns
* Website-based recommendations
* Targeted promotions

The exact strategy can be refined further using additional customer behaviour and campaign data.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **SciPy**
* **Jupyter Notebook**

### Machine Learning Concepts

* Exploratory Data Analysis
* Feature Engineering
* Feature Encoding
* Feature Scaling
* PCA
* K-Means Clustering
* Agglomerative Clustering
* Elbow Method
* Silhouette Score
* Cluster Profiling

---

## 📁 Project Structure

```text
SmartCart/
│
├── SmartCart.ipynb
└── README.md
```

---

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd SmartCart
```

### 2. Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

### 3. Open the notebook

```bash
jupyter notebook SmartCart.ipynb
```

Run the notebook cells sequentially to reproduce the analysis.

---

## 📌 Key Takeaway

This project helped me understand the practical workflow of **unsupervised machine learning**, particularly how preprocessing, feature engineering, dimensionality reduction, clustering, and cluster interpretation come together in a real customer-segmentation problem.

The main takeaway was that clustering doesn't end with assigning customers to groups. The more important step is understanding **what those groups represent and how the resulting segments can be translated into meaningful business insights.**

---

## 👨‍💻 Author

**Krish Arora**

B.Tech CSE (AI-ML)
PIET, Samalkha

[GitHub](https://github.com/krisharora7) • [LinkedIn](https://www.linkedin.com/in/krish-arora07/)
