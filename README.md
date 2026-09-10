# 🛒 SmartKart AI Retention Engine

### AI-Powered Customer Churn Prediction & Retention Analytics

SmartKart AI Retention Engine is a machine learning–based customer analytics solution designed to identify customers who are at risk of churn.

The project uses customer-level data to clean and preprocess business data, detect anomalies and outliers, and build a **Logistic Regression classification model** to predict whether a customer is likely to churn.

The objective is to help SmartKart's retention team identify high-risk customers early and take proactive customer retention actions.

---

## 🎯 Business Problem

SmartKart, an online retail company, is facing several customer-retention challenges:

* Some customers are no longer purchasing.
* Marketing campaigns receive a low response.
* Customer complaints are increasing.
* Management does not know which customers require immediate attention.
* The company wants to use AI to identify customers who may stop purchasing.

### Business Objective

Build a predictive machine learning solution that can identify customers with a higher likelihood of churn, allowing SmartKart to prioritize retention efforts.

---

## 💡 Solution

The SmartKart AI Retention Engine follows an end-to-end machine learning pipeline:

**Raw Customer Data → Data Inspection → Data Cleaning → Outlier Treatment → Feature Selection → Target Definition → Train-Test Split → Standardization → Logistic Regression → Churn Prediction → Model Evaluation → Business Insights**

The notebook implements a 15-step ML pipeline covering data preprocessing through final model interpretation.

---

## 📊 Dataset

The project uses:

`SmartKart_dirty_100_rows.csv`

The dataset contains **100 customer records and 5 columns**:

| Feature         | Description                                             |
| --------------- | ------------------------------------------------------- |
| `Customer_ID`   | Unique customer identifier                              |
| `Age`           | Customer age                                            |
| `Monthly_Spend` | Customer's monthly spending                             |
| `Complaints`    | Number of customer complaints                           |
| `Churn`         | Target variable indicating whether the customer churned |

The dataset was intentionally created as a **dirty dataset** containing real-world-style data-quality problems such as missing values, duplicate records, invalid entries, and outliers.

---

## 🧹 Data Cleaning

Before model development, the dataset is inspected and cleaned.

The pipeline handles:

* Duplicate customer records
* Missing values
* Leading/trailing whitespace
* Incorrect data types
* Text-based numeric values
* Invalid customer ages
* Negative monthly spending
* Extreme values and outliers

For example, the raw dataset contains duplicate records, missing values, an invalid negative spending value, unrealistic ages, and extreme spending/complaint values.

After duplicate removal, the dataset contains **95 records**. Missing values are handled using median imputation.

---

## 📈 Outlier Treatment

The project uses the **Interquartile Range (IQR) method** to detect extreme observations.

Instead of automatically deleting customers with extreme values, identified outliers are capped so that potentially useful customer records are retained.

This is particularly relevant because Logistic Regression can be influenced by extreme feature values.

---

## 🤖 Machine Learning Model

### Logistic Regression

The project uses **Logistic Regression** as the classification algorithm.

The model predicts the probability that a customer belongs to the churn class:

* `0` → Customer retained
* `1` → Customer churned

The model is appropriate for this project because the business objective is a **binary classification problem**.

---

## 🔄 Machine Learning Pipeline

### 1. Data Collection

Load the SmartKart customer dataset.

### 2. Data Understanding

Inspect:

* Dataset dimensions
* Data types
* Missing values
* Duplicate records
* Statistical characteristics

### 3. Data Cleaning

Resolve data-quality issues and prepare usable customer records.

### 4. Outlier Detection & Treatment

Use the IQR method to identify and cap extreme values.

### 5. Feature Selection

Select relevant customer attributes for model development.

### 6. Target Definition

Define `Churn` as the prediction target.

### 7. Target Encoding

Convert the target into a machine-learning-compatible binary format.

### 8. Train-Test Split

Divide the dataset into training and testing subsets.

### 9. Feature Standardization

Standardize numerical features before model training.

### 10. Model Building

Create the Logistic Regression classifier.

### 11. Model Training

Train the model using the prepared training data.

### 12. Prediction

Generate churn predictions for unseen/test customers.

### 13. Model Evaluation

Evaluate predictive performance using classification metrics.

### 14. Model Interpretation

Interpret model results and identify important churn-related patterns.

### 15. Final Output

Generate actionable churn-risk information for customer retention.

The complete notebook follows these 15 stages from data collection through final output.

---

## 📌 Key Business Value

The SmartKart AI Retention Engine can help the business:

* Identify customers at risk of leaving
* Prioritize high-risk customers
* Support proactive retention campaigns
* Improve customer relationship management
* Reduce potential customer loss
* Convert customer data into actionable business intelligence

Instead of treating every customer equally, the system enables the retention team to focus resources on customers who are predicted to have a higher churn risk.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** — Data manipulation
* **NumPy** — Numerical operations
* **Matplotlib** — Data visualization
* **Seaborn** — Visualization
* **Scikit-learn** — Machine learning
* **Google Colab** — Development environment
* **Logistic Regression** — Classification model

---

## 📁 Project Structure

```text
SmartKart-AI-Retention-Engine/
│
├── SmartKart_dirty_100_rows.csv
│
├── SmartKart_Churn_Prediction_ML_Pipeline.ipynb
│
├── smartkart_churn_risk_report.csv
│
└── README.md
```

### Files

**`SmartKart_dirty_100_rows.csv`**
Original intentionally messy customer dataset.

**`SmartKart_Churn_Prediction_ML_Pipeline.ipynb`**
Complete machine learning pipeline from data collection to churn prediction.

**`smartkart_churn_risk_report.csv`**
Customer-level churn-risk output generated from the analysis.

---

## 📊 Model Evaluation

The model is evaluated using appropriate classification metrics to understand how effectively it identifies churn and non-churn customers.

Typical evaluation outputs in the notebook include:

* Confusion Matrix
* Accuracy
* Precision
* Recall
* F1-Score
* Classification performance analysis

The focus is not only on overall accuracy but also on the model's ability to identify customers who are likely to churn.

---

## 🚀 How to Run

### Option 1 — Google Colab

1. Open the `.ipynb` notebook in Google Colab.
2. Upload `SmartKart_dirty_100_rows.csv` when prompted.
3. Run the notebook from top to bottom.
4. Review the data-cleaning outputs.
5. Review the model evaluation results.
6. Review the final churn-risk predictions.

### Option 2 — Local Python Environment

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Then launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the SmartKart notebook and run the cells sequentially.

---

## 🔍 Example Business Interpretation

A customer predicted as **high churn risk** can be prioritized by the retention team for actions such as:

* Personalized offers
* Customer-service follow-up
* Complaint resolution
* Targeted retention campaigns
* Personalized communication

The model therefore acts as a **decision-support system**, helping management determine which customers should receive attention first.

---

## ⚠️ Project Limitations

This project is a demonstration of an end-to-end churn prediction workflow using a small, intentionally messy dataset.

The dataset contains only **100 original customer records and five variables**, so the model should not be treated as a production-ready enterprise churn system without further validation on larger and more representative customer data.

For production deployment, the solution could be extended with:

* Larger customer datasets
* Purchase frequency
* Recency of last purchase
* Marketing campaign response
* Customer lifetime value
* Product/category preferences
* Digital engagement
* Payment behavior
* Advanced ML models
* Model monitoring and retraining

---

## 🔮 Future Scope

The SmartKart AI Retention Engine can be further developed into a complete customer-retention platform by adding:

### Predictive Risk Scoring

Assign each customer a numerical churn probability.

### Customer Segmentation

Divide customers into groups such as:

* Low Risk
* Medium Risk
* High Risk

### Automated Retention Recommendations

Recommend appropriate retention actions based on customer behavior.

### Advanced Machine Learning

Compare Logistic Regression with models such as:

* Decision Tree
* Random Forest
* Gradient Boosting
* XGBoost

### Business Dashboard

Build an interactive dashboard showing:

* Total customers
* Churn rate
* High-risk customers
* Customer spending
* Complaint trends
* Retention opportunities

---

## 🎓 Academic Context

**Course:** Introduction to AI & ML
**Program:** BBA AI/ML / FinTech & AI
**Institution:** Chitkara Business School

**Core Learning Outcome:**
Apply data preprocessing, feature selection, machine learning models, and appropriate evaluation metrics to solve business problems.

---

## 👨‍💻 Project

**SmartKart AI Retention Engine**

> *Turning customer data into proactive retention decisions through machine learning.*

---

## ⭐ Keywords

`Customer Churn` `Churn Prediction` `Machine Learning` `Artificial Intelligence` `Customer Retention` `Predictive Analytics` `Logistic Regression` `Data Cleaning` `Data Preprocessing` `Business Analytics` `SmartKart` `Python`
