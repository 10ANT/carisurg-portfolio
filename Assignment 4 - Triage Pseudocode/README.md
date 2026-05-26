# Assignment 4 - Triage Pseudocode

## Objective

Design a digital triaging system that processes patient data and categorizes them into risk levels.

---

## Approach

This assignment uses **blood pressure** and **oxygen saturation (SpO2)** to determine patient risk levels based on the Emergency Severity Index (ESI) framework.

---

## Input Parameters

| Parameter | Unit | Normal Range |
|-----------|------|--------------|
| Systolic BP (SBP) | mmHg | 90-120 |
| Diastolic BP (DBP) | mmHg | 60-80 |
| Oxygen Saturation (SpO2) | % | 95-100 |

---

## Risk Thresholds

### Blood Pressure

| Category | SBP | DBP | Risk |
|----------|-----|-----|------|
| Severe Hypotension | < 80 | < 50 | Critical |
| Moderate Hypotension | 80-89 | 50-59 | Emergent |
| Normal | 90-120 | 60-80 | Low |
| Hypertensive Crisis | ≥ 180 | ≥ 120 | Critical |

### Oxygen Saturation

| Category | SpO2 | Risk |
|----------|------|------|
| Severe Hypoxemia | < 85% | Critical |
| Moderate Hypoxemia | 85-89% | Emergent |
| Mild Hypoxemia | 90-94% | Urgent |
| Normal | 95-100% | Low |

---

## Algorithm Pseudocode

```python
def calculate_triage_level(sbp, dbp, spo2):
    # Input validation
    if any input is NULL:
        return "ERROR"
    
    # Assess each vital sign
    bp_risk = assess_blood_pressure(sbp, dbp)
    oxygen_risk = assess_oxygen_saturation(spo2)
    
    # Worst case prevails
    overall_risk = max(bp_risk, oxygen_risk)
    return map_to_triage_category(overall_risk)
```

---

## Triage Categories (ESI)

| Level | Category | Max Wait | Color |
|-------|----------|----------|-------|
| 1 | Resuscitation | 0 min | RED |
| 2 | Emergent | 10 min | ORANGE |
| 3 | Urgent | 30 min | YELLOW |
| 4 | Less Urgent | 60 min | GREEN |
| 5 | Non-Urgent | 120 min | BLUE |

---

## Files

| File | Description |
|------|-------------|
| `Digital_Triage_Pseudocode.pdf` | Complete pseudocode document for submission |

---

## Key Design Principles

1. **Critical conditions first** - Check for life-threatening values immediately
2. **Worst case prevails** - Use the highest risk level from any parameter
3. **Clinical thresholds** - Based on established medical guidelines
4. **ESI compatible** - Output aligns with international triage standards

---

**Author:** CariSurg MedTech Pathways | Week 0
