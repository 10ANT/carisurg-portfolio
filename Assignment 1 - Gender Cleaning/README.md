# Assignment 1 - Gender Cleaning

## Objective

Clean and standardize the Gender column in the Emergency Triage Dataset.

---

## Problem

The Gender column contained inconsistent values that needed to be standardized for analysis.

### Before Cleaning

| Value | Count |
|-------|-------|
| `0` | ~450 |
| `1` | ~480 |
| `Male` | ~380 |
| `MALE` | ~120 |
| `Female` | ~350 |
| `FEMALE` | ~100 |

---

## Solution

Applied a mapping function to convert all values to standardized binary encoding:

```python
gender_map = {
    'Male': 1, 'MALE': 1, '1': 1,
    'Female': 0, 'FEMALE': 0, '0': 0
}
df['Gender'] = df['Gender'].map(gender_map)
```

### After Cleaning

| Value | Meaning |
|-------|---------|
| `0` | Female |
| `1` | Male |

---

## Results

- **6 different representations → 2 standardized values**
- **No missing values after cleaning**
- **Final data type: int64**

---

## Files

| File | Description |
|------|-------------|
| `Week0_Tutorial1_EnvSetup_and_Cleaning_Gender.ipynb` | Jupyter notebook with complete cleaning process |

---

## Key Takeaways

1. Data cleaning is essential before analysis
2. Real-world data often contains inconsistencies
3. Mapping functions provide a clean solution for standardization

---

**Author:** CariSurg MedTech Pathways | Week 0
