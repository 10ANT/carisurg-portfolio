# Assignment 2 - Pulse Cleaning

## Objective

Clean the pulse column by handling data type issues, outliers, and missing values.

---

## Problem

The pulse column contained several data quality issues:

- Non-numeric values (`'error'` strings)
- Physiologically impossible values (outliers)
- Missing values (NaN)

---

## Methodology

### Step 1: Type Conversion

Convert all values to numeric, coercing errors to NaN:

```python
df['pulse'] = pd.to_numeric(df['pulse'], errors='coerce')
```

### Step 2: Outlier Removal

Remove physiologically impossible values (outside 20-250 bpm):

```python
df.loc[(df['pulse'] < 20) | (df['pulse'] > 250), 'pulse'] = np.nan
```

### Step 3: Imputation

Fill missing values with median (more robust than mean):

```python
df['pulse'] = df['pulse'].fillna(df['pulse'].median())
```

---

## Results

### Final Statistics

| Statistic | Value |
|-----------|-------|
| Mean | 88.00 bpm |
| Median | 88.00 bpm |
| Std Dev | 19.88 bpm |
| Min | 40.00 bpm |
| Max | 170.00 bpm |

### Clinical Distribution

| Category | Range | Percentage |
|----------|-------|------------|
| Bradycardia | < 60 bpm | ~5% |
| Normal | 60-100 bpm | ~60% |
| Tachycardia | > 100 bpm | ~35% |

---

## Files

| File | Description |
|------|-------------|
| `Week0_Tutorial2_Advanced_Cleaning.ipynb` | Jupyter notebook with cleaning process |
| `Pulse_Vital_Sign_Report.docx` | Comprehensive report on pulse vital sign |

---

## Key Takeaways

1. Always validate data types before analysis
2. Use clinical knowledge to identify impossible values
3. Median imputation is more robust than mean for vital signs
4. Tachycardia is common in ED patients (~35%)

---

**Author:** CariSurg MedTech Pathways | Week 0
