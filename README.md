# Data Processing Module

This repository contains the Python module **`data_processing.py`**, designed to help with loading CSV files, organizing them into table-like structures, performing filtering, and computing aggregated statistics.  
Below is an expanded and detailed explanation of every component in the script so you can clearly understand how each part works.

---

##  Overview

The module includes:

1. **DataLoader** – Reads CSV files into Python structures.
2. **Table** – A lightweight table processor for filtering, printing, and aggregating.
3. **Example Workflow** – Demonstrates how these classes are intended to be used.

This README explains each part in detail.

---

##  1. DataLoader Class

### **Purpose**
To load CSV data from a specified directory and convert it into a list of dictionaries where each row becomes a dictionary.

### **Key Features**
- Automatically resolves the directory where your Python file is located.
- Allows setting a custom base path for loading files.
- Converts CSV rows into dictionaries using `csv.DictReader`.

### **Important Methods**

#### **`__init__(self, base_path=None)`**
- If `base_path` is not provided, it automatically sets the directory of the script as the working path.
- If provided, it converts the custom path into a valid `Path` object.

#### **`load_csv(self, filename)`**
- Joins the base path with the filename.
- Opens the CSV file safely.
- Reads the file and loads each row as a dictionary.
- Returns a list of dictionaries containing your data.

---

##  2. Table Class

This class is designed to help process lists of dictionaries like a simple dataset.

### **Key Abilities**
- Print rows cleanly.
- Filter data using flexible lambda conditions.
- Return new Table objects for method chaining.
- Perform aggregations such as min or max.

### **Important Methods**

#### **`print_table(self, n=10)`**
- Prints the first `n` rows.
- Helps check loaded data before processing.

#### **`filter(self, condition)`**
- Accepts a lambda function (e.g., `lambda x: x['EU'] == 'yes'`)
- Returns a **new Table instance** with only matching rows.
- Allows chaining:
  ```python
  table.filter(...).filter(...)
  ```

#### **`aggregate(self, func, column)`**
- Extracts column values.
- Applies a function (e.g., `min`, `max`, `sum`).
- Returns the computed result.

---

##  3. Example Usage in the Script

The example section shows how to use the module:

### **1. Load data**
```python
my_loader = DataLoader()
my_table1 = Table(my_loader.load_csv("cities.csv"))
```

### **2. Preview a portion of the table**
```python
my_table1.print_table(5)
```

### **3. Filter example**
```python
my_table_filtered = my_table1.filter(lambda x: x['EU'] == 'no')
```
This returns only non‑EU countries.

### **4. Multi‑step filtering**
```python
my_table3_filtered = (
    my_table3
    .filter(lambda x: x['EU'] == 'yes')
    .filter(lambda x: x['coastline'] == 'no')
)
```

### **5. Aggregation**
```python
min_temp = my_table3_filtered.aggregate(lambda x: min(x), 'temperature')
max_temp = my_table3_filtered.aggregate(lambda x: max(x), 'temperature')
```

---

##  Project Structure

```
data_processing.py
README.md
your_csv_files/
```

Place all your CSV files inside `your_csv_files/` or the same folder as the script.

---

##  Running the Script

Use:

```bash
python3 data_processing.py
```

The script will:
- Load the CSV files
- Filter according to provided conditions
- Print results
- Compute min/max temperatures for required cases

---

##  Requirements

- Python **3.8+**
- No external packages required

---

##  Author
This README was generated with expanded explanations for clarity based on your request.