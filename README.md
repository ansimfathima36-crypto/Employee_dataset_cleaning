# Employee Data Cleaning using Python

## 📌 Project Overview

This project focuses on cleaning and preprocessing an employee dataset using **Python, Pandas, and NumPy**.

The main goal is to identify and handle common data quality issues such as **missing values, duplicate records, incorrect data types, inconsistent values, invalid values, and outliers**.

## 🛠️ Tools & Technologies

* Python
* Pandas
* NumPy
* Jupyter Notebook

## 📂 Dataset

The dataset contains employee-related information such as:

* Name
* Age
* Department
* Salary
* Experience
* City
* Joining Year

## 🔍 Data Cleaning Steps

### 1. Data Loading

Loaded the employee dataset using Pandas.

```python
df = pd.read_csv("employee_data.csv")
```

### 2. Data Overview

Used the following functions to understand the dataset:

* `head()`
* `info()`
* `shape`
* `describe()`

### 3. Handling Missing Values

Checked missing values using:

```python
df.isnull().sum()
```

Different methods were used based on the column:

* **Age** → Mean
* **Department** → Mode
* **Salary** → Median
* **Experience** → Mean

An invalid age value of **-5** was first converted into `NaN` before handling the missing value.

### 4. Handling Duplicate Values

Checked for duplicate records and identified duplicates based on employee-related columns.

Duplicate records were removed using:

```python
df = df.drop_duplicates(
    subset=["Name", "Age", "Department", "Salary",
            "Experience", "City", "Joining_Year"]
)
```

### 5. Handling Data Types

Checked the data types using:

```python
df.dtypes
```

Converted:

* Age → Integer
* Experience → Integer

### 6. Handling Inconsistent Data

Standardized text values in the **City** and **Department** columns.

Operations used:

* `.str.lower()`
* `.str.strip()`
* `.map()`

Example:

```python
df["City"] = df["City"].str.lower().str.strip()
```

City values were standardized to:

* Chennai
* Coimbatore

Department values were standardized to:

* Data
* HR
* IT

### 7. Detecting Outliers

Used the **IQR (Interquartile Range)** method to identify salary outliers.

```python
Q1 = df["Salary"].quantile(0.25)
Q3 = df["Salary"].quantile(0.75)

IQR = Q3 - Q1
```

Lower and upper limits were calculated using:

```python
lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR
```

Salary values outside these limits were identified as outliers.

## 📊 Final Result

After the cleaning process, the dataset was prepared by:

* Handling missing values
* Removing duplicate records
* Correcting invalid values
* Converting data types
* Standardizing inconsistent categorical values
* Detecting salary outliers

## 🎯 Learning Outcomes

Through this project, I practiced important **Data Cleaning and Data Preprocessing** techniques using Python.

This project helped me understand how raw employee data can be transformed into a more consistent and analysis-ready dataset.

## 👩‍💻 Author

**Ansim Fathima**

B.Sc Data Science
