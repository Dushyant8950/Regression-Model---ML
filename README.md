# Regression-Model---ML
This code is a machine learning workflow for predicting property prices using various regression algorithms. Here’s a breakdown of the steps involved:

**1. Data Loading and Preprocessing**
- The dataset **"PropertyPrice_Data.csv"** is loaded into a pandas DataFrame (`df`).
- The data is split into **train (80%)** and **test (20%)** sets using `train_test_split()`.
- A new column **"Source"** is created to distinguish between train and test sets.
- Both datasets are combined into a single dataset (`fullRaw`) for preprocessing.

**2. Data Cleaning and Encoding**
- The **"Id"** column is dropped as it does not contribute to model prediction.
- Missing values are checked using `isnull().sum()`.
- Categorical variables are **one-hot encoded** using `pd.get_dummies()`.

**3. Splitting Data Back into Train & Test Sets**
- The train and test datasets are separated based on the **"Source_Train"** column.
- The dependent variable **("Sale_Price")** is extracted into `trainY` and `testY`.
- The independent variables are stored in `trainX` and `testX`.

---

**4. Machine Learning Models**
**1. Decision Tree Regressor**
- A **Decision Tree Regressor** is trained on `trainX` and `trainY`.
- Predictions are made on the test set.
- Performance is evaluated using:
  - **Root Mean Squared Error (RMSE)**
  - **Mean Absolute Percentage Error (MAPE)**
  
**2. Random Forest Regressor**
- A **Random Forest Regressor** is trained and tested similarly.
- Performance metrics show better results compared to the Decision Tree.

**3. K-Nearest Neighbors (KNN) Regressor**
- A **KNN Regressor** is applied without standardization.
- It performs worse than Decision Tree and Random Forest.

**4. Standardizing Data for KNN**
- **StandardScaler** is used to normalize `trainX` and `testX`.
- KNN is retrained on the standardized data (`trainX_Std`).
- Performance improves compared to the unscaled version.

---

**5. Key Observations**
- **Random Forest** performs best with **lowest RMSE (36,194) and MAPE (11.41%)**.
- **KNN without standardization** performs poorly.
- **KNN with standardization** improves but still isn't the best model.
