# Vehicle Resale Price Prediction

This repository contains code for predicting vehicle resale prices using various regression models. The dataset used for this project contains features such as vehicle age, mileage, engine size, body type, and gas emissions.

## Table of Contents

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Dataset](#dataset)
- [Data Preprocessing](#data-preprocessing)
- [Modeling](#modeling)
  - [Polynomial Regression](#polynomial-regression)
  - [Decision Tree Regression](#decision-tree-regression)
  - [Random Forest Regression](#random-forest-regression)
  - [Gradient Boosting Regression](#gradient-boosting-regression)
  - [XGBoost Regression](#xgboost-regression)
  - [Neural Network](#neural-network)
- [Results](#results)
- [Key Takeaways](#key-takeaways)
- [License](#license)

## Getting Started

### Prerequisites

- Python 3.x
- Pandas
- Scikit-learn
- Seaborn
- Matplotlib
- XGBoost
- Keras

### Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/hemanth08/CarResalePrediction.git
    ```
2. Navigate to the project directory:
    ```sh
    cd CarResalePrediction
    ```
3. Install the required packages:
    ```sh
    pip install -r requirements.txt
    ```

### Dataset

The dataset should be saved as `Final_df0504.csv`. Make sure this file is located in the root directory of the project.

## Data Preprocessing

1. Load the dataset:
    ```python
    import pandas as pd

    O_df = pd.read_csv("Final_df0504.csv")
    ```
2. Drop unnecessary columns:
    ```python
    df = O_df.drop(['Genmodel', 'Genmodel_id', "Adv_id", 'Maker'], axis="columns")
    ```
3. One-hot encode categorical columns:
    ```python
    def one_hot_encode(df):
        object_cols = df.select_dtypes(include=['object']).columns
        dummy_cols = pd.get_dummies(df[object_cols], drop_first=True)
        df_encoded = df.drop(object_cols, axis=1)
        df_encoded = pd.concat([df_encoded, dummy_cols], axis=1)
        return df_encoded

    df_encoded = one_hot_encode(df)
    ```

## Modeling

### Polynomial Regression

1. Split the data into training and testing sets.
2. Create polynomial features.
3. Fit a linear regression model.
4. Evaluate the model using R² score.

### Decision Tree Regression

1. Split the data into training and testing sets.
2. Fit a decision tree regressor.
3. Optimize the model using GridSearchCV.
4. Evaluate the model using R² score.

### Random Forest Regression

1. Split the data into training and testing sets.
2. Fit a random forest regressor.
3. Optimize the model using GridSearchCV.
4. Evaluate the model using R² score.

### Gradient Boosting Regression

1. Split the data into training and testing sets.
2. Fit a gradient boosting regressor.
3. Optimize the model through trial and error.
4. Evaluate the model using R² score.

### XGBoost Regression

1. Split the data into training and testing sets.
2. Fit an XGBoost regressor.
3. Evaluate the model using R² score.

### Neural Network

1. Create a sequential neural network model.
2. Add input, hidden, and output layers.
3. Compile and train the model.
4. Evaluate the model using Mean Squared Error (MSE) and R² score.

## Results

- Polynomial Regression: Train R² = 0.870, Test R² = 0.870
- Decision Tree Regression: Train R² = 0.977, Test R² = 0.955 (max_depth=10)
- Random Forest Regression: Train R² = 0.993, Test R² = 0.970 (n_estimators=100, max_depth=20)
- Gradient Boosting Regression: Train R² = 0.977, Test R² = 0.959 (n_estimators=50, learning_rate=0.3, max_depth=5)
- XGBoost Regression: Train R² = 0.993, Test R² = 0.970
- Neural Network: Train R² = 0.984, Test R² = 0.976

## Key Takeaways

1. Years, Runned Miles, Entry Price, Bodytype, and Gas-emission are the most significant features determining the resale price of a vehicle.
2. The models explain most of the variance in the dataset.
3. There were no over-fitting issues found.
4. All ensemble methods yield similar results around 96%.
5. The high MSE values can be attributed to the high price values in the target column.
6. Decision Trees give the best possible outcomes given computational/time constraints, while XGBoosting gives the best predictions overall with 97% accuracy.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
