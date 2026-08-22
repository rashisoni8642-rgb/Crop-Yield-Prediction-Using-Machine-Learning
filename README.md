# Crop-Yield-Prediction-Using-Machine-Learning
Crop Yield Prediction using Machine Learning is a data science project that predicts the expected crop yield of a particular region using factors such as rainfall, temperature, humidity, soil conditions, crop type, and other agricultural parameters. Regression algorithms can be trained to learn the relationship between agricultural factors.
# Crop Yield Prediction Using Machine Learning

**Project Overview**

This project focuses on predicting **crop yield using machine learning** by analyzing historical agricultural, environmental, and crop-related data. The model uses information such as **crop type, geographical area, year, average annual rainfall, pesticide usage, and average temperature** to predict crop yield.

The target variable is **`hg/ha_yield`**, which represents crop yield measured in **hectograms per hectare (hg/ha)**. The project implements an **XGBoost Regression** model to learn the relationship between these input factors and crop yield.

## Objective

The main objective of this project is to develop a machine learning model capable of predicting crop yield from historical agricultural and environmental factors. Such predictions can support agricultural planning, resource management, and crop production analysis.

## Dataset

The project contains the following datasets:

### 1. `yield.csv`

This is the crop-yield dataset containing historical yield information.

Important fields include:

* **Domain** – Data domain, such as Crops.
* **Area** – Country or geographical area.
* **Element** – Type of measurement, such as Yield.
* **Item** – Crop type, such as Maize, Potatoes, Rice, Sorghum, Soybeans, and Wheat.
* **Year** – Year of the observation.
* **Unit** – Measurement unit, such as `hg/ha`.
* **Value** – Recorded crop yield.

The dataset contains historical crop-yield observations for different areas, crops, and years.

### 2. `rainfall.csv`

This dataset contains yearly average rainfall information for different geographical areas.

Fields include:

* **Area** – Country or geographical area.
* **Year** – Year of the observation.
* **average_rain_fall_mm_per_year** – Average annual rainfall measured in millimeters per year.

For example, the dataset contains rainfall records for countries such as Afghanistan, Albania, and Algeria.

### 3. `temp.csv`

This dataset contains average temperature information by country and year.

Fields include:

* **year** – Year of the observation.
* **country** – Country or geographical area.
* **avg_temp** – Average temperature.

The dataset also contains some missing temperature values for certain country-year observations.

### 4. `pesticides.csv`

This dataset contains pesticide-use information by geographical area and year.

Fields include:

* **Domain** – Data domain.
* **Area** – Country or geographical area.
* **Element** – Type of measurement.
* **Item** – Pesticide category.
* **Year** – Year of the observation.
* **Unit** – Measurement unit.
* **Value** – Pesticide usage.

The pesticide values are recorded in **tonnes of active ingredients**.

### 5. `yield_df.csv`

`yield_df.csv` is the prepared dataset used directly by the machine learning notebook.

It contains the following fields:

| Column                          | Description                |
| ------------------------------- | -------------------------- |
| `Area`                          | Geographical area/country  |
| `Item`                          | Crop type                  |
| `Year`                          | Year of observation        |
| `hg/ha_yield`                   | Target crop yield in hg/ha |
| `average_rain_fall_mm_per_year` | Average annual rainfall    |
| `pesticides_tonnes`             | Pesticide usage in tonnes  |
| `avg_temp`                      | Average temperature        |

Examples in the dataset show crop-wise observations for Albania, including Maize, Potatoes, Rice, Soybeans, and Wheat, together with rainfall, pesticide usage, temperature, and yield values.

## Machine Learning Workflow

The project follows these main steps:

```text
Dataset
   ↓
Data Loading
   ↓
Data Cleaning
   ↓
Remove Unnecessary Column
   ↓
Encode Categorical Features
   ↓
Separate Features and Target
   ↓
Train-Test Split
   ↓
XGBoost Regression
   ↓
Prediction
   ↓
Model Evaluation
```

## Data Preprocessing

The notebook loads `yield_df.csv` using Pandas and removes the unnecessary `Unnamed: 0` column.
The categorical columns **`Area`** and **`Item`** are converted into numerical representations. The notebook first demonstrates Label Encoding and later uses **One-Hot Encoding (`pd.get_dummies`)** in the final model implementation.
The target variable is:

```text
hg/ha_yield
```

and the remaining columns are used as input features.

## Train-Test Split

The dataset is divided into:

* **80% training data**
* **20% testing data**

using `train_test_split` with `random_state=42`.

## Machine Learning Model

The project uses **XGBoost Regressor (`XGBRegressor`)** for crop-yield prediction.

The notebook initially defines the model with:

* `n_estimators = 500`
* `learning_rate = 0.05`
* `max_depth = 6`
* `random_state = 42`

and trains it on the training dataset.

The final implementation also trains an `XGBRegressor` after applying one-hot encoding to the categorical variables.

## Model Evaluation

The model is evaluated using:

* **R² Score**
* **Mean Squared Error (MSE)**
* **Root Mean Squared Error (RMSE)**

The final notebook implementation produced:

| Metric             |            Result |
| ------------------ | ----------------: |
| R² Score           |        **0.9759** |
| Mean Squared Error | **174,599,952.0** |
| RMSE               |     **13,213.63** |

These are the results recorded in the uploaded Colab notebook.
An **Actual vs Predicted Crop Yield** scatter plot is also generated to visually compare the model's predictions with the actual values.

## Technologies Used

* Python
* Google Colab
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* Matplotlib

## Project Structure

```text
Crop-Yield-Prediction/
│
├── CropYield.ipynb
├── yield.csv
├── rainfall.csv
├── temp.csv
├── pesticides.csv
├── yield_df.csv
└── README.md
```

## Google Colab Notebook

The complete machine learning implementation is available in the Colab notebook:

**[Open in Google Colab](YOUR_COLAB_LINK_HERE)**

The notebook contains the data loading, preprocessing, model training, prediction, evaluation, and visualization steps used in this project.

## Conclusion

This project demonstrates the application of **machine learning regression for crop-yield prediction** using historical crop, rainfall, pesticide, temperature, geographical, and temporal information. The implemented XGBoost model achieved an **R² score of approximately 0.976** on the test set in the provided notebook, indicating a strong fit on this dataset.

The project provides a foundation for further work such as comparing multiple regression algorithms, improving feature engineering, analyzing feature importance, and evaluating the model on additional agricultural data.
