# **Case Study: Optimizing E-Commerce Sales Data Analysis with DataAnalysts vs. Traditional Pandas & NumPy**

## **Introduction**

Data cleaning and preprocessing are fundamental steps in data analytics. Traditional methods using **pandas** and **NumPy** require multiple lines of code to handle missing values, outliers, type conversions, and other preprocessing tasks. The **DataAnalysts** library simplifies and accelerates this process by allowing data analysts to clean, transform, and visualize data using **intuitive one-liners**.

This case study compares traditional data preprocessing techniques with the **DataAnalysts** library while working on a large **E-Commerce Sales dataset (10,000 rows)**. We will demonstrate how DataAnalysts **reduces complexity and improves efficiency**, making it a powerful alternative for data professionals.

---

## **Dataset Overview**

The dataset consists of **10,000 e-commerce transactions** from 2023 to 2024, including the following columns:

- **Customer\_ID** – Unique identifier for each customer.
- **Purchase\_Date** – Date of purchase.
- **Product\_Category** – Category of the purchased product.
- **Purchase\_Amount** – Amount spent in dollars.
- **Customer\_Age** – Age of the customer.
- **Location** – Customer's city.
- **Gender** – Male (M) / Female (F).
- **Total\_Purchases** – Total number of purchases made by the customer.
- **Discount\_Applied** – Discount percentage applied to the purchase.

---

# **Comparison: Traditional Pandas vs. DataAnalysts**

## **Step 1: Loading the Dataset**

### **Traditional Pandas**

```python
import pandas as pd

# Load dataset
df = pd.read_excel("ecommerce_sales_data.xlsx")

# Check dataset structure
df.info()
```

### **Using DataAnalysts**

```python
import dataanalysts as da

# Load dataset using DataAnalysts
df = da.excel("ecommerce_sales_data.xlsx")

# Quick summary of dataset
da.summary(df)
```

✅ **DataAnalysts Advantage:**\
With **da.summary(df)**, we instantly get an overview of missing values, column types, and key statistics in **one line** instead of multiple pandas commands.

---

## **Step 2: Handling Missing Values**

### **Traditional Pandas**

```python
# Filling missing values with median for numerical columns
df["Purchase_Amount"].fillna(df["Purchase_Amount"].median(), inplace=True)
df["Customer_Age"].fillna(df["Customer_Age"].median(), inplace=True)

# Filling missing values with mode for categorical columns
df["Gender"].fillna(df["Gender"].mode()[0], inplace=True)
df["Location"].fillna(df["Location"].mode()[0], inplace=True)
```

### **Using DataAnalysts**

```python
df = da.clean(df, strategy="handle_missing", missing_strategy="median")
```

✅ **DataAnalysts Advantage:**\
Instead of multiple `.fillna()` statements, **da.clean()** automatically applies the best missing value handling strategy in a single line.

---

## **Step 3: Removing Duplicates**

### **Traditional Pandas**

```python
df.drop_duplicates(inplace=True)
```

### **Using DataAnalysts**

```python
df = da.clean(df, strategy="remove_duplicates")
```

✅ **DataAnalysts Advantage:**\
Both methods are simple, but **da.clean()** maintains a structured workflow across different cleaning steps.

---

## **Step 4: Fixing Data Types**

### **Traditional Pandas**

```python
# Converting columns to appropriate data types
df["Purchase_Date"] = pd.to_datetime(df["Purchase_Date"])
df["Purchase_Amount"] = df["Purchase_Amount"].astype(float)
df["Customer_Age"] = df["Customer_Age"].astype(int)
```

### **Using DataAnalysts**

```python
df = da.clean(df, strategy="convert_dtype", column="Purchase_Date", dtype="datetime")
df = da.clean(df, strategy="convert_dtype", column="Purchase_Amount", dtype="float")
df = da.clean(df, strategy="convert_dtype", column="Customer_Age", dtype="int")
```

✅ **DataAnalysts Advantage:**\
Handles datatype conversion **systematically**, maintaining **clear readability** across operations.

---

## **Step 5: Data Visualization**

### **Traditional Pandas + Matplotlib**

```python
import matplotlib.pyplot as plt

plt.hist(df["Purchase_Amount"], bins=20, color="skyblue", edgecolor="black")
plt.xlabel("Purchase Amount")
plt.ylabel("Frequency")
plt.title("Purchase Amount Distribution")
plt.show()
```

### **Using DataAnalysts**

```python
da.histogram(df, column="Purchase_Amount", bins=20)
```

✅ **DataAnalysts Advantage:**\
Handles **visualization automatically** with default styling and formatting.

---

## **Key Findings & Conclusion**

### **Why is DataAnalysts More Efficient?**

| Feature        | Traditional Pandas/NumPy | DataAnalysts                              |
| -------------- | ------------------------ | ----------------------------------------- |
| Missing Values | Multiple `.fillna()`     | `da.clean(strategy="handle_missing")`     |
| Duplicates     | `drop_duplicates()`      | `da.clean(strategy="remove_duplicates")`  |
| Data Types     | `.astype()` methods      | `da.clean(strategy="convert_dtype")`      |
| Outliers       | Manual IQR calculations  | `da.clean(strategy="handle_outliers")`    |
| Text Cleaning  | `.str.strip()` methods   | `da.clean(strategy="fix_structural")`     |
| Encoding       | Manual `LabelEncoder()`  | `da.clean(strategy="encode_categorical")` |
| Visualization  | `matplotlib` code        | `da.histogram()`                          |

✅ **Faster Processing:** Reduces code complexity by **50-70%**.\
✅ **Intuitive Syntax:** Consistent **one-liner commands** for all data operations.\
✅ **Beginner-Friendly:** Requires **minimal coding effort** compared to pandas.\
✅ **Production-Ready:** Can handle **large datasets (10k+ rows)** efficiently.

---

## **Final Verdict**

The **DataAnalysts** module significantly simplifies and accelerates **data cleaning, transformation, and visualization** tasks. Its **intuitive functions** reduce the time required for preprocessing, making it an **ideal choice for data analysts and ML practitioners** looking for a streamlined solution.

---

🚀 **Next Steps**

- **Future Versions**: Integrating **one-line ML model training** (e.g., `da.linearregression(df, "TargetColumn")`).
- **Community Growth**: Open-sourcing the module and gathering feedback for **continuous improvements**.

---

## **📌 Summary**

The **DataAnalysts** library offers an **efficient, readable, and user-friendly** alternative to traditional pandas-based data processing. Whether you're a beginner or an experienced analyst, **this tool can revolutionize your data workflow.**


