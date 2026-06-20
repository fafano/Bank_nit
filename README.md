# Nooshirvani Bank Dataset Processing Project

## 📋 Project Overview

This project processes and analyzes the **Nooshirvani Bank dataset** using **Python** and **Pandas**. It includes 20 different tasks covering data cleaning, statistical analysis, pattern recognition, and financial rule enforcement.

---

## ⚠️ Important Note

**The dataset file (`Bank NIT DB.csv`) is NOT included in this repository due to its large size (~3 GB).**

To run this project, you need to:
1. Obtain the dataset from your instructor or data provider
2. Place the file in the root directory of the project
3. Ensure the filename matches `Bank NIT DB.csv`

---

## 🛠️ Technologies Used

- **Python 3**
- **Pandas**: Data processing and analysis
- **NumPy**: Numerical computations
- **Matplotlib**: Data visualization
- **Regex**: Pattern matching and search

---

## 📁 File Structure

```
Nooshirvani_Bank.ipynb
├── Task 1: Random Record Scanning
├── Task 2: Filling Empty Residence Fields
├── Task 3: National Code Standardization
├── Task 4: Fraud Detection (Alizadeh in Hormozgan)
├── Task 5: Adding Dormitory Address
├── Task 6: Bank Card Number Generation
├── Task 7: Searching for "Hosseini Mahdavi"
├── Task 8: Finding Names Starting with "Vania"
├── Task 9: Age Comparison (1290s vs 1390s)
├── Task 10: Finding People with Same Birth Date
├── Task 11: Persian Letters in Father's Name
├── Task 12: Residents of Khalkhal in Ardabil
├── Task 13: Standard Surnames (DFA)
├── Task 14: Loan Acceptance (NFA)
├── Task 15: Specific Surname Patterns (DFA)
├── Task 16: High-Risk Customer Detection (NFA)
├── Task 17: Dormitory Wealth Distribution
├── Task 18: Account Blocking (>100 Billion Rials)
├── Task 19: Special Customers in Markazi Province
└── Task 20: Finding Relatives
```

---

## 🎯 Key Features

### Data Processing
- **Chunk-based processing**: Handles large datasets (33+ million records) efficiently
- **Regex patterns**: Advanced pattern matching for Persian text
- **Data cleaning**: Removes empty values, standardizes formats

### Pattern Recognition
- **DFA (Deterministic Finite Automaton)**: Surname pattern validation
- **NFA (Nondeterministic Finite Automaton)**: Multi-condition customer analysis
- **Turing Machine**: Account balance validation

### Financial Analysis
- **Wealth distribution**: Fair distribution among dormitory residents
- **High-risk detection**: Multi-conditional risk assessment
- **Account blocking**: Automatic blocking of accounts above threshold

---

## 📊 Sample Results

| Task | Description | Result |
|------|-------------|--------|
| Task 4 | Alizadeh in Hormozgan | 327 people found |
| Task 8 | Names starting with "Vania" | 426 people found |
| Task 9 | Age comparison | 1,149 (1290s) vs 437,702 (1390s) |
| Task 12 | Khalkhal residents | 28,903 people found |
| Task 16 | High-risk customers | 740,104 people found |
| Task 18 | Blocked accounts | 11,935,189 accounts |

---

## 🚀 How to Run

### Prerequisites
```bash
pip install pandas numpy matplotlib
```

### Steps
1. **Download the dataset** and place it in the project root:
   ```
   /project-root/
   ├── Nooshirvani_Bank.ipynb
   └── Bank NIT DB.csv    <-- You need to add this file
   ```

2. Open the Jupyter Notebook:
```bash
jupyter notebook Nooshirvani_Bank.ipynb
```

3. Run cells sequentially from top to bottom

4. The processed file will be saved as `Bank NIT DB.csv` (overwritten)

---

## 📝 Dataset Details

- **Original file**: `Bank NIT DB.csv`
- **File size**: ~3 GB (not included in repository)
- **Total records**: ~32 million
- **Columns**:
  - `national_code`: National ID (standardized to 10 digits)
  - `FULL_NAME`: Full name
  - `FATHER_NAME`: Father's name
  - `BIRTH_DATE`: Birth date (YYYY-MM-DD)
  - `CITY_NAME`: Current city
  - `PROVINCE_NAME`: Current province
  - `BIRTH_CITY`: Birth city
  - `BIRTH_PROVINCE`: Birth province
  - `ADDRESS`: Address (added in Task 5)
  - `CARD_NUMBERS`: Bank card number (added in Task 6)
  - `ACCOUNT_BALANCE`: Account balance (added in Task 17)

---

## 🔍 Key Algorithms

### 1. DFA for Surname Validation (Task 13)
```
States: 0 (Start), 1 (Accept), 2 (Checking 'ر'), 3 (Checking 'پور')
Accept Condition: Surname ends with "ی" OR "پور"
```

### 2. NFA for High-Risk Detection (Task 16)
```
Conditions:
  a: Surname "Asghari" or "Jafari" + Birth year 1360-1380
  b: Province: Sistan-Baluchistan, Hormozgan, or Khuzestan
  c: First name contains "ز" or "ن"
Risk Level: High if 2+ conditions are met
```

### 3. Turing Machine for Balance Validation (Task 18)
```
Input: Account balance as string
States:
  q0: Check first digit is '1'
  q1: Check remaining digits are '0'
Accept: Exactly "100000000000" (100 billion)
Reject: Any other 12+ digit number
```

---

## 📈 Visualization

Task 9 includes a bar chart comparing average ages between people born in the 1290s and 1390s.

```python
# Average Age Comparison
1290-1299: ~104 years
1390-1399: ~14 years
```

---

## 💾 Memory Management

The dataset is processed in **chunks of 1 million records** to prevent memory issues:

```python
for chunk in pd.read_csv(file_path, chunksize=1_000_000):
    # Process each chunk
    pass
```

This approach:
- Prevents memory overflow
- Handles the 3GB file efficiently
- Maintains performance on standard hardware

---

## ⚠️ Important Notes

1. **Dataset Not Included**: The 3GB dataset file is not uploaded to GitHub
2. **Encoding**: All files use `utf-8` encoding with `utf-8-sig` for proper Persian text handling
3. **Data Type**: All columns are read as `str` to prevent type conversion errors
4. **Regex**: Persian letters (ی, ک) are used; Arabic equivalents (ي, ك) are handled separately
5. **File Overwrite**: The processing scripts overwrite the original CSV file

---

## 🔧 Customization

You can modify the following parameters:

```python
# Chunk size for memory management
chunk_size = 1_000_000  # Adjust based on your RAM

# File paths
file_path = "Bank NIT DB.csv"  # Change if your file has different name

# Regex patterns (modify as needed)
pattern = re.compile(r'your_pattern_here')
```

---

## License

This project is for educational purposes. Feel free to use and modify for learning MIPS pipeline architecture.