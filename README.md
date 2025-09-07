# 🛢️ Oil Well Development Modeling  
*Bootstrapped linear regression modeling to identify the optimal region for oil well development under risk constraints.*  

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)  
![pandas](https://img.shields.io/badge/pandas-EDA-green?logo=pandas)  
![numpy](https://img.shields.io/badge/numpy-Numerical-blue?logo=numpy)  
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)  
![matplotlib](https://img.shields.io/badge/matplotlib-Visualization-orange?logo=matplotlib)  
![seaborn](https://img.shields.io/badge/seaborn-EDA-blue?logo=python)  
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)  
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)  

---

## 📌 Overview  
OilyGiant is considering new oil well developments across three candidate regions. The objective of this project was to:  

1. **Predict the profitability of wells** using features describing subsurface conditions (`f0`, `f1`, `f2`).  
2. **Estimate development ROI** by modeling revenues against a fixed well development cost.  
3. **Apply bootstrapping** to quantify risk of loss across 1,000 simulations.  
4. Recommend the optimal region for development where:  
   - Average profit is maximized, and  
   - Risk of loss is **< 2.5%** (company threshold).  

---

## 📊 Dataset  
- **Source:** TripleTen Bootcamp (simulated oil field data)  
- **Regions:** Three separate datasets (Region 0, 1, 2), each with:  
  - `f0, f1, f2` — subsurface features  
  - `product` — oil reserves (thousands of barrels)  
- **Feature Engineering:**  
  - `revenue` = product × \$4,500 (per 1,000 barrels)  
  - `op_ex` = \$100M ÷ 200 wells (fixed per well)  
  - `net_profit` = revenue – op_ex  
  - `roi` = net_profit ÷ op_ex  

---

## ⚙️ Methods & Tools  
- **Libraries:** pandas, NumPy, scikit-learn, matplotlib, seaborn  
- **Techniques:**  
  - Data cleaning and feature engineering  
  - Correlation analysis of subsurface features vs. product & profit  
  - **Linear Regression** modeling with custom 5-fold cross-validation  
  - **Bootstrapped profit simulation** (1,000 iterations with replacement, selecting top 200 wells out of 500 each run)  
  - Evaluation metrics: Average Profit, 95% CI, Risk of Loss %  

---

## 📈 Results  
- **Break-even threshold:** ~111k barrels per well. All three regions fell below this on average, requiring bootstrapped simulations.  
- **Cross-validation:** Linear regression models trained on all three regions, but residuals showed signs of underfitting.  
- **Bootstrapped Profit Simulation Summary:**  

| Region   | Avg Profit | 95% CI                       | Risk of Loss | Meets Criteria? |
|----------|------------|------------------------------|---------------|-----------------|
| Region 0 | \$4.82M    | [-\$0.59M, \$9.87M]         | **3.7%** ❌   | No              |
| Region 1 | \$4.31M    | [\$0.46M, \$8.40M]          | **1.4%** ✅   | Yes             |
| Region 2 | \$3.62M    | [-\$1.81M, \$8.84M]         | **9.4%** ❌   | No              |  

---

## 💡 Key Insights  
- **Region 1** is the only viable option:  
  - Positive average profit (\$4.31M).  
  - Risk of Loss below 2.5% (1.4%).  
- **Region 0** and **Region 2** showed higher average profits at first glance, but bootstrapping revealed unacceptably high risk of loss.  
- Bootstrapping was essential to stress-test profitability under real-world variability.  

---

## 🗂 Repo Structure  
```
oil-well-development-modeling/
├── notebooks/ <- Final cleaned Jupyter notebook
├── data/ <- Region datasets
├── requirements.txt <- Dependencies
├── LICENSE <- MIT License
└── README.md <- This file
```

---

## 🚀 How to Run  
1. Clone the repo:  
   ```bash
   git clone https://github.com/Flamingo-Rocker/oil-well-development-modeling.git
   cd oil-well-development-modeling
2. Install dependencies:
    ```bash
    pip install -r requirements.txt
3. Open the notebook in `/notebooks` to reproduce the analysis.

---

## 📦 Requirements
```
pandas==2.3.2
numpy==2.2.5
numpy-base==2.2.5            
numpydoc==1.9.0            
matplotlib==3.10.5           
matplotlib-base==3.10.5           
matplotlib-inline==0.1.6
seaborn==0.13.2
scipy==1.16.0     
scikit-learn==1.7.1         
ipython==8.30.0
```

---

## 🙏 Acknowledgment
Developed as part of the TripleTen Data Science Bootcamp, applying regression modeling, cross-validation, and bootstrapping to evaluate oil well development risk and profitability.
