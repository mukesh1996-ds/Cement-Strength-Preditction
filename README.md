# Cement Strength Prediction

## Overview

This project aims to develop a regression model to predict **concrete compressive strength** based on various cement mixture components and their properties. The model leverages advanced machine learning techniques, including clustering and model selection, to provide accurate predictions tailored to specific data clusters.

---

## Problem Statement

Concrete compressive strength is a critical parameter in construction and material science. Predicting this strength helps optimize mixtures, ensuring durability and cost efficiency. The goal is to build a regression model that accurately predicts this strength based on the components and age of the mixture.

---

## Data Description

The dataset includes the following features:

| **Feature**               | **Type**       | **Unit**        | **Description**                                                                 |
|----------------------------|----------------|-----------------|---------------------------------------------------------------------------------|
| Cement (component 1)       | Quantitative   | kg/m³ mixture   | Main binding material in the concrete mix.                                     |
| Blast Furnace Slag (2)     | Quantitative   | kg/m³ mixture   | Byproduct with silicates and aluminosilicates enhancing durability.            |
| Fly Ash (3)                | Quantitative   | kg/m³ mixture   | Combustion byproduct improving workability and strength.                       |
| Water (4)                  | Quantitative   | kg/m³ mixture   | Essential for cement hydration and mix workability.                            |
| Superplasticizer (5)       | Quantitative   | kg/m³ mixture   | Additive to reduce water content and enhance strength.                         |
| Coarse Aggregate (6)       | Quantitative   | kg/m³ mixture   | Larger particles providing strength and bulk.                                  |
| Fine Aggregate (7)         | Quantitative   | kg/m³ mixture   | Smaller particles filling gaps for smoother mix.                               |
| Age                        | Quantitative   | Days (1–365)    | Time since concrete preparation.                                               |
| Concrete Compressive Strength | Quantitative | MPa             | Target variable representing the concrete's strength.                          |

---

## Workflow

Below is the end-to-end flow of the project:
D:\Data Science\Cement-Strength-Preditction\Workflow_Image\WorkFLow.png

<<<<<<< HEAD

=======
>>>>>>> d539b10cc153a71039e3bcf7add6d88da2fd0649

### Data Validation
1. **File Validation:**
   - **Name Validation**: Ensures filenames match the schema.
   - **Column Count**: Confirms column count matches schema.
   - **Column Names and Data Types**: Validates column structure as per schema.
   - **Null Checks**: Identifies and moves files with missing data to the `Bad_Data_Folder`.

2. **Folder Segregation**:
   - Valid files are moved to the `Good_Data_Folder`.
   - Invalid files are moved to the `Bad_Data_Folder`.

### Data Preprocessing
- Handle missing values using **KNN Imputer**.
- Apply **log transformations** to normalize data.
- Scale features using standard scaling techniques.

### Clustering
- Use **KMeans Clustering** to group data into clusters.
- Determine the optimal number of clusters via **Elbow Method** and **KneeLocator**.

### Model Training
- Train separate models for each cluster using:
  - **Random Forest Regressor**
  - **Linear Regression**
- Select the best model per cluster based on R² scores.

### Prediction
1. Preprocess incoming data using trained preprocessing pipelines.
2. Assign clusters using the KMeans model.
3. Predict compressive strength using the corresponding cluster's model.

---

## Deployment

The project is deployed using **Pivotal Web Services**. Key deployment components include:
- **`main.py`**: Entry point for the Flask server.
- **`Procfile`**: Specifies the app's entry point.
- **`requirements.txt`**: Lists all Python dependencies.
- **`runtime.txt`**: Specifies the Python version.

### Steps:
1. Install **Pivotal Cloud Foundry CLI** and configure the environment.
2. Use the `cf push` command to deploy the app.
3. Validate functionality using **Postman** or similar tools.

---

## Folder Structure

```plaintext
Cement_Strength_Prediction/
├── data/
│   ├── Good_Data_Folder/
│   └── Bad_Data_Folder/
├── models/
│   ├── kmeans_model.pkl
│   ├── cluster_1_model.pkl
│   └── cluster_2_model.pkl
├── logs/
│   ├── data_validation.log
│   └── model_training.log
├── app/
│   ├── main.py
│   ├── predictionFromModel.py
│   ├── requirements.txt
│   ├── Procfile
│   └── runtime.txt
├── schema/
│   └── schema_training.json
└── README.md
```

---

## How to Run

### Prerequisites
- Python 3.x
- Required packages listed in `requirements.txt`

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/username/Cement_Strength_Prediction.git
   cd Cement_Strength_Prediction
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Start the application:
   ```bash
   python app/main.py
   ```
4. Use Postman to send prediction requests or access the UI endpoint.

---

## Key Features
- Comprehensive data validation pipeline.
- Dynamic clustering for optimized model performance.
- Scalable architecture for incremental data updates.
- Deployment-ready with Pivotal Web Services integration.

---

## Future Enhancements
- Add support for more advanced regression algorithms.
- Integrate visualization tools for better interpretability.
- Develop an API for easier data submission and retrieval.

---

Feel free to refine this as per your specific requirements or preferences!
