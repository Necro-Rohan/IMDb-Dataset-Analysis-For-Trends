# 🎬 IMDb & TMDb Movie Industry Analysis

## 📌 Project Overview
This project provides a comprehensive data mining analysis of the global film industry spanning from **1960 to 2025**. By merging the structural depth of the **IMDb Official Dataset** with the financial metrics of the **TMDb Dataset**, this analysis uncovers hidden patterns in movie profitability, casting chemistry, and directorial success.

The project goes beyond simple visualization, employing **Association Rule Mining (Apriori)** and **DBSCAN Clustering** to identify what statistically drives a movie to be a "Hit" or a "Flop."

---

## 🔍 Key Insights & Discovery

### 1. The "Invisible Ceiling" of Profitability
* **Insight:** Profitability does not scale linearly with budget.
* **Data:** The **Apriori Algorithm** revealed that `HIT` status (ROI > 300%) is overwhelmingly associated with `LOW_BUDGET` films.
* **Conclusion:** Profitability scales with **constraint**, not investment. Horror and Documentary genres offer the safest ROI ratios.

### 2. The "Christopher Nolan" Effect
* **Insight:** While critics prefer older legends (Kubrick), Nolan is the undisputed king of modern audience engagement.
* **Data:** He holds 3 of the top 6 spots for most-voted movies (*The Dark Knight, Inception, Interstellar*), proving he bridges the gap between "Art House quality" and "Blockbuster scale."

### 3. The 80/20 Financial Rule (DBSCAN)
* **Insight:** The industry is split into two distinct clusters.
* **Cluster 0 (80%):** Mainstream films with predictable, modest financial returns.
* **Cluster -1 (20%):** Extreme outliers containing both the massive blockbusters and the catastrophic flops.
* **Conclusion:** Financial volatility is driven entirely by the "outlier" class.

### 4. Actor Chemistry & Franchise Power
* **Top Duo:** Cameron Diaz & Eddie Murphy (Hit Ratio: 1.0) due to the *Shrek* franchise.
* **The "Mid-Rating Anchors":** Actors like **Jude Law** and **Jennifer Lawrence** statistically stabilize a movie's rating between 6.5–7.9, acting as a hedge against critical failure.

---

## 🛠️ Tech Stack & Methodology

| Component | Libraries / Tools |
| :--- | :--- |
| **Data Processing** | `Pandas`, `NumPy` |
| **Visualization** | `Matplotlib`, `Seaborn` |
| **Market Basket Analysis** | `Mlxtend` (Apriori Algorithm) |
| **Clustering** | `Scikit-learn` (DBSCAN, StandardScaler) |
| **Data Source** | IMDb Official Interfaces & TMDb API |

---

## 📂 Repository Structure

```text
├── notebooks/          # Jupyter Notebooks containing the analysis
│   └── 01_IMDb_Financial_Mining.ipynb
├── data.md             # Instructions on downloading the dataset
└── README.md           # Project documentation
````

-----

## 🚀 Getting Started

### 1\. Prerequisites

Install the required Python libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn mlxtend
```

### 2\. Data Setup

Due to the massive size of the dataset (\~9GB), the raw files are **not** included in this repo.

  * Read `data.md` in this repository for specific download links and instructions on where to place the files.

### 3\. Running the Analysis

Navigate to the `notebooks/` folder and launch the Jupyter Notebook:

```bash
jupyter notebook notebooks/01_IMDb_Financial_Mining.ipynb
```

-----

## 📊 Methodology Highlights

### ✔ Data Stratification

Separated the dataset into two distinct views:

  * **`df_general`** → Content-based analysis.
  * **`df_financial`** → ROI & profitability analysis.
  * *Why:* This approach improves accuracy by avoiding the 50% of movies with missing financial values.

### ✔ Feature Engineering

Created categorical bins to enable rule mining:

  * **ROI:** `Hit` / `Flop`
  * **Duration:** `Long` / `Short`
  * **Budget:** `Low` / `Mid` / `High`

### ✔ Association Rules

Used `mlxtend.apriori` to discover high-confidence rules such as:

  * `{Drama, Short Duration} → {Low Budget}`
  * *Why:* This helps in understanding statistical relationships between genres, runtime, and financial patterns.

### ✔ Outlier Detection

Applied **DBSCAN** to separate:

  * **Cluster 0:** Standard industry performers.
  * **Cluster -1:** High-risk / high-reward financial anomalies.
  * *Why:* This cleans the regression data by separating typical movies from extreme financial outliers.

-----

## 📜 License

This project uses data from **IMDb** and **TMDb**. Please refer to their respective non-commercial licensing agreements before reuse.
