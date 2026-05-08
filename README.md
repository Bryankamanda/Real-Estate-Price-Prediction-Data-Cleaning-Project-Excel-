
#  Real Estate Price Prediction – Data Cleaning Project (Excel)

##  Project Overview

This project focuses on cleaning and transforming a **messy real-world Kenyan real estate dataset** into a structured, machine-learning-ready format using **Microsoft Excel only**.

The dataset contained unstructured text, inconsistent formatting, and missing values. The goal was to apply **data cleaning and feature engineering techniques** to prepare it for house price prediction modeling.

---

#  Data Cleaning & Feature Engineering Process

---

## 1. Extracting Number of Bedrooms

###  Task:

Extract bedroom count from property title.

###  Example:

`6 Bed Villa with En Suite → 6`

###  Formula:

```excel id="bed1"
=VALUE(LEFT(A2,FIND(" ",A2)-1))
```

---

## 2. Extracting Property Type

###  Task:

Extract property type from title.

###  Example:

`6 Bed Villa with En Suite → Villa`

###  Formula:

```excel id="ptype1"
=TEXTBEFORE(TEXTAFTER(A2," Bed "), " with")

```

---

## 3. Extracting Location

###  Task:

Extract main area from multi-location field.

###  Example:

`Spring Valley, Westlands → Westlands`

###  Formula:

```excel id="loc1"
=TRIM(RIGHT(SUBSTITUTE(B2,",",REPT(" ",100)),100))
```

---

## 4. Has Gym (Binary Encoding)

###  Task:

Check if gym is mentioned in description/title.

###  Formula:

```excel id="gym1"
=IF(ISNUMBER(SEARCH("gym",A2)),1,0)
```

---

## 5. En Suite Feature

###  Task:

Detect en suite presence.

###  Formula:

```excel id="ensuite1"
=IF(OR(ISNUMBER(SEARCH("en suite",A2)),ISNUMBER(SEARCH("ensuite",A2))),1,0)
```

---

## 6. Swimming Pool Feature

###  Formula:

```excel id="pool1"
=IF(ISNUMBER(SEARCH("pool",A2)),1,0)
```

---

## 7. Has DSQ

###  Task:

Extract DSQ from description column.

###  Formula:

```excel id="dsq1"
=IF(ISNUMBER(SEARCH("dsq",C2)),1,0)
```

---

## 8. Has Garden

###  Formula:

```excel id="garden1"
=IF(ISNUMBER(SEARCH("garden",C2)),1,0)
```

---

## 9. Has Parking

###  Formula:

```excel id="park1"
=IF(ISNUMBER(SEARCH("parking",C2)),1,0)
```

---

## 10. Cleaning Selling Price (Target Variable)

###  Task:

Remove currency symbols and convert to numeric.

###  Example:

`KSh 130,000,000 → 130000000`

###  Formula:

```excel id="price1"
=IFERROR(VALUE(SUBSTITUTE(SUBSTITUTE(I2,"KSh ",""),",","")),"")
```

---

## 11. Handling Missing Property Type

###  Task:

Replace missing values.

###  Formula:

```excel id="ptype2"
=IF(A2="","NOT PROVIDED",A2)
```

---

## 12. Final Dataset Freeze (No Formulas)

* Copied all columns
* Pasted as **values only**
* Removed dependency on Excel formulas

---

#  Final Dataset Structure

| Feature       | Description            |
| ------------- | ---------------------- |
| Bedrooms      | Extracted from title   |
| Property Type | Villa, Apartment, etc. |
| Has Gym       | 1/0                    |
| En Suite      | 1/0                    |
| Swimming Pool | 1/0                    |
| Has DSQ       | 1/0                    |
| Has Garden    | 1/0                    |
| Location      | Main area extracted    |
| Selling Price | Clean numeric target   |

---

#  Tools Used

* Microsoft Excel
* Excel Functions:

  * `SEARCH`
  * `SUBSTITUTE`
  * `VALUE`
  * `IFERROR`
  * `TRIM`
  * `LEFT`
  * `MID`
  * `FIND`
  * `RIGHT`

---

#  Skills Demonstrated

* Real-world messy data cleaning
* Feature engineering from unstructured text
* Binary encoding of categorical features
* Handling missing values
* Target variable preprocessing
* Excel-based data pipeline development

---

#  Outcome

The final dataset is:

* Clean
* Structured
* ML-ready

It can be used for:

* House price prediction models (Regression)
* Power BI dashboards
* Feature importance analysis
* Data-driven real estate insights in Kenya

---

#  Next Steps

* Build ML model in Python (Linear Regression / Random Forest)
* Perform exploratory data analysis (EDA)
* Identify key price drivers
* Deploy prediction model
* Build Power BI dashboard

---

#  Author

**Bryan Kamanda**

