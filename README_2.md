# Machine-Learning-Approach-to-Predict-Drug-exposure-with-PK-and-Pharmacogenomic-PGx-variability.
developed a simple machine learning model that predics Area Under the Curve (AUC) using

Clearance (CL)
Volume of Distribution (V)
Genetic metabolizer status (slow vs fast)

The goal is to show how a patient’s genotype can affect drug clearance, and how clearance can influence overall drug exposure measured by AUC.

I created a simulated patient dataset, added basic patient details, calculated AUC, and trained a machine learning model to predict AUC using patient-level variables.

## Project idea

In pharmacokinetics, patients do not always clear a drug at the same speed. Some patients may be slow metabolizers, while others may be fast metabolizers. This difference can affect how much drug stays in the body.

In this project:

- AUC is calculated using clearance
- A Random Forest model is trained to predict AUC

> Lower clearance means higher AUC. Higher clearance means lower AUC.

## Dataset

The dataset is simulated, not real patient data.

Each row represents one patient. The dataset includes:

| Column | Meaning |
|---|---|
| genotype | Whether the patient is a slow or fast metabolizer |
| cl | Clearance of the drug |
| V | Volume of distribution |
| AUC | Area under the curve, which represents total drug exposure |
| patient_id | Fake patient ID generated using Faker |
| age | Randomly generated patient age |
| sex | Randomly assigned sex |

## AUC formula

AUC was calculated using:

```python
AUC = Dose / Clearance
```

In this project, the dose was kept constant. So clearance becomes the main factor affecting AUC.


## Machine learning model

I used `RandomForestRegressor` from scikit-learn.

The model was trained using:

- Clearance
- Volume of distribution
- Encoded genotype

The target variable:

- AUC

The data was split into training and testing sets. The model learned from the training data and was evaluated on the test data.

## Why Random Forest?

the relationship is already very clear because AUC was created from clearance. So the model performs very well mainly because clearance directly controls AUC.

## Result interpretation

The model result showed a very high R² score and low error.

This means the predicted AUC values were very close to the actual AUC values.

However, this does not mean the model is ready for clinical use. The dataset is simulated, and the formula is simple. This project is mainly for learning how pharmacogenomics, pharmacokinetics, and machine learning can be connected.

## New patient prediction

The model then predicts the expected AUC for that patient.

genotype and clearance should make biological sense together. For example, a slow genotype usually has lower clearance, while a fast genotype usually has higher clearance.

## Tools used

- Python
- NumPy
- pandas
- Faker
- scikit-learn
- joblib
- Jupyter Notebook

## Files

| File | Description |
|---|---|
| pgx-2.ipynb | Main notebook |
| simulated_data.csv | Simulated patient dataset |
| model file | Saved Random Forest model, if exported using joblib |

## project is for educational purpose
 It uses simulated data.
