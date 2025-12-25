# Task B: Transformation Logic & Business Rules

### Detailed Rules
![Transformation Rules](images/TransformationRules.png)


## Rule 1: Unit Standardization
- **Logic:** If unit = "W", divide by 1000 → convert to "kW"
- **Reason:** Ensures consistent units across all records.

## Rule 2: Handling Missing Values
- **Logic:** If reading is NULL, interpolate using neighboring values.
- **Flag:** If large gaps exist, mark as "Gap" and exclude from peak calculations.

## Rule 3: Data Validation
- **Logic:** Negative or unrealistically high readings (>50 kW for small houses) are marked as "Error".

## Rule 4: Faulty Meter Detection
- **Logic:** Meter reporting exactly 0.00 kW for 24 hours during extreme weather → "Potential Faulty Meter".
