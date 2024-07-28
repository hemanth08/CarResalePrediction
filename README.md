# Vehicle Price Prediction

## Problem Statement
Develop a machine learning model that accurately predicts the price of a vehicle based on its features.

## Data Sources
- **DVM Car Dataset**: A large-scale dataset for Automotive Applications maintained by the University of Glasgow, University of Southern California, and University of Lincoln. [DVM Car Dataset](https://deepvisualmarketing.github.io/)
- **US Historic Monthly Inflation Data**: Historical inflation rates from 1914-2023. [US Inflation Calculator](https://www.usinflationcalculator.com/inflation/historical-inflation-rates/)
- **US Gas Prices Monthly**: U.S. retail gasoline prices (dollars per gallon). [EIA Gas Prices](https://www.eia.gov/dnav/pet/hist/LeafHandler.ashx?n=pet&s=emm_epm0_pte_nus_dpg&f=m)

## Data Preprocessing
- **Merging Tables**: The DVM car dataset was initially split into 7 different CSV files. The tables were merged using Excel.
- **Handling Missing Values**:
  - Replaced zeros with NaN in specific columns: Engine_size, Wheelbase, Height, Length, Door_num, Sales, Gas_Emissions.
  - Imputed missing values using values from rows with matching Genmodel_id.
  - Dropped columns with high NA percentages: Color, Last_produced_year.
  - Cleaned non-numeric characters from numeric columns and converted them to float.
  - Created a new feature 'Years' by subtracting registration year from advertised year.

## Feature Engineering
- Applied one-hot encoding to categorical variables.
- Conducted correlation analysis to identify significant features.
- Saved the cleaned dataset to `Final_df0504.csv`.

## Modeling
### Polynomial Regression
- Achieved train R² score: 0.870
- Achieved test R² score: 0.870
- High multicollinearity observed among features.

### Decision Trees
- Initial model:
  - Train R² score: 0.998
  - Test R² score: 0.964
- Optimized with GridSearchCV:
  - Best hyperparameters: max_depth=14
  - Train R² score: 0.992
  - Test R² score: 0.964

### Random Forest Regressor
- Initial model:
  - Train R² score: 0.993
  - Test R² score: 0.970
- Optimized with GridSearchCV:
  - Best hyperparameters: n_estimators=100, max_depth=20
  - Train R² score: 0.993
  - Test R² score: 0.970

### Gradient Boosting Regressor
- Initial model:
  - Train R² score: 1.000
  - Test R² score: 0.965
- Optimized model:
  - Train R² score: 0.977
  - Test R² score: 0.959

### XGBoost Regressor
- Model:
  - Train R² score: 0.993
  - Test R² score: 0.970

### Fully Connected Neural Network
- Model:
  - Train R² score: 0.977
  - Test R² score: 0.959
- Observed that the model performs less effectively compared to ensemble methods and decision trees.

## Key Takeaways
1. Significant features determining the resale price of a vehicle include Years, Runned Miles, Entry Price, Bodytype, and Gas-emission.
2. Ensemble methods, particularly Random Forest and XGBoost, provided the best performance.
3. High multicollinearity among features can affect model performance.

## Conclusion
The project demonstrates the effective use of various machine learning algorithms to predict vehicle prices. Ensemble methods, especially Random Forest and XGBoost, showed the best results in terms of R² scores and overall performance.

## Future Work
1. Addressing multicollinearity among features to improve model robustness.
2. Exploring additional feature engineering techniques.
3. Using larger and more diverse datasets for better generalization.

## Dependencies
- Python
- pandas
- numpy
- seaborn
- matplotlib
- scikit-learn
- xgboost
- keras

## Usage
1. Clone the repository.
2. Ensure all dependencies are installed.
3. Run the Jupyter Notebook or Python scripts to replicate the analysis and model training.

## Acknowledgments
- University of Glasgow, University of Southern California, and University of Lincoln for the DVM Car Dataset.
- US Inflation Calculator and EIA for additional data.
