# M2P16 Capstone Project
--------

**Summary/Objective:** <br>
This project will involve supervised regression models to **predict the price of a laptop** based on a dataset containing various laptop features. The dataset includes information such as screen size, RAM, CPU, GPU, storage and other specifications. Each model is trained and evaluated to compare their performance in predicting laptop prices, with the goal of determining the most accurate model for this task.

**Reference link for data set:** <br>
https://www.kaggle.com/datasets/owm4096/laptop-prices


**Three supervised regression models will be used:**
1. Multiple Linear Regression with Ridge Regularization
2. Random Forest Regression
3. Support Vector Regression (SVR)

**The material applied from Module 2 will be the following:**
1. Feature Engineering and Data Preprocessing
2. Linear Regression
3. Regularization
4. Decision Trees and Random Forests
5. Support Vector Regression (SVR)

**The project will be split into five parts:**
1. Part 1 will involve EDA, Visualization, Data Cleaning, Encoding, Data Preparation (ex: Split to X and y).  <br>
2. Part 2 will be working with Model #1: Multiple Linear Regression with Ridge Regularization. <br>
3. Part 3 will be working with Model #2: Random Forest Regression. <br>
4. Part 4 will be working with Model #3: Support Vector Regression (SVR). <br>
5. Part 5 will be determining which of the three models has the best performance and having the best performing model be our final model. <br>
   The final model will be used to make a prediction and includes some final comments/conclusion. <br>
   The final model will also be deployed and loaded to make a prediction. <br>

**M2P16 Capstone Project criteria:** <br>
1. **EDA includes verifying missing data (null values) and checking values dtypes (ex: object, float64, int64, etc.)** <br>

    *<u>Observations from EDA:* <br>
- There are no missing values. <br>
- 'Inches', 'Ram', 'Weight', 'Price_euros', 'ScreenW', 'ScreenH', 'CPU_freq', 'PrimaryStorage', 'SecondaryStorage' are numerical (float64 and int64). <br> 
- The other features which are objects will either be removed or will be converted to be numeric (int, float). <br> 

2. **Visualization include a countplot, boxplot, scatterplot, pairplot and correlation heatmap (only for top 20 correlations).** <br>

    *<u>Observations from Visualization:</u>* <br>
- Windows 10 has the highest count for OS (Operating System).
- For 'TypeName' (or laptop type), Workstations, Ultrabooks and Gaming laptops tend to have the highest prices.
- An increase in Screen Sizes, RAM and CPU_freq tend to have an increase in price.   
- Features such as 'Ram', 'ScreenW', 'ScreenH' and 'CPU_freq' are among the highest correlations with the price.

3. **Cleaning and preparing data:** <br>

- Data preparation includes splitting data into X and y. <br>

    *<u>Dropping Unnecessary Features:</u>* <br>
- 'Company' and 'Product' will be removed as they do not provide valuable information regarding laptop specifications (like CPU, RAM, screen resolution, and storage) which could affect the price.
- 'Touchscreen', 'IPSpanel', 'RetinaDisplay' are very specific for certain laptop brands. They may not provide useful insights for modeling or could be considered redundant in terms of identifying key features.


4. **Feature Engineering** <br>

    *<u>Encoding categorical data (with One Hot Encoder):</u>* <br>
- Regression models require numerical data (as input) to understand patterns to provide a predictive output. <br> 
- 'TypeName', 'OS', 'Screen', 'CPU_company', 'CPU_model', 'PrimaryStorageType', 'SecondaryStorageType', 'GPU_company', 'GPU_model' were converted from object to numerical values with One Hot Encoder. <br>

    *<u>Scaling for 2 of the 3 models (using StandardScaler):</u>* <br>
- Multiple Linear Regression with Ridge Regularization has scaling due to the regularization term penalizing the coefficients based on their size. <br>
- Random Forest Regression <u>does not require scaling</u> because it is based on decision trees, which split the data based on feature values rather than using distances or calculations affected by scale. <br>
- Support Vector Regression (SVR) requires scaling because the algorithm relies on distances between data points to find the optimal hyperplane.

5. **The 3 Supervised Regression Models and their Advantages:** <br>

    <u>Multiple Linear Regression with Ridge Regularization</u> <br>

- MLR with Ridge helps overcome issues like multicollinearity and overfitting. <br>
- It is computationally efficient and works well with noisy data. <br> 
    
    <u>Random Forest Regression</u> <br>

- RFR combines multiple decision trees to improve accuracy and reduce overfitting, making it robust to noise and capable of capturing complex patterns in data. <br>
- It also automatically handles missing values and can model non-linear relationships without needing extensive feature engineering. <br> 
    
    <u>Support Vector Regression (SVR)</u> <br>

- SVR efficiently handles high-dimensional data, can model non-linear relationships using the kernel trick, and is robust to overfitting, especially when the number of features is greater than the number of data points.
- It also focuses on minimizing errors within a specified margin, leading to better generalization.

6. **Validation scheme:** <br>
- Cross-validation (with GridSearchCV) was used as a validation scheme. Cross-validation was used to evaluate the holdout data for the final model, and has similar results/metrics with the test data.<br>

7. **Features chosen for final model:** <br>

- 'Inches', 'Ram', 'Weight', 'ScreenW', 'ScreenH', 'CPU_freq', 'PrimaryStorage', 'SecondaryStorage' <br>
- Hot Encoded features chosen: 'TypeName', 'OS', 'Screen', 'CPU_company', 'CPU_model', 'PrimaryStorageType', 'SecondaryStorageType', 'GPU_company', 'GPU_model' <br>
- Reason for chosen features: Features which deal with screen size and technical specifications (OS, CPU, GPU, RAM, Storage, etc.) were chosen as they could influence the price. 

8. **Final model used for prediction (and deployment):**
- Of the three models, the Random Forest Regression model had the best performance as it has the best metrics.
- As per prediction experimentation, with "new_data_df" (data frame)" as input, the Random Forest Regression Model was able to provide a prediction of the laptop price (in euros). <br>
- The final model was deployed as a joblib file (as 'M2P16_rfr_model.joblib'). After loading the final model, the final model ('M2P16_rfr_model.joblib') was able to make a prediction. <br>

## Conclusion 
In conclusion, three models were tested: Multiple Linear Regression with Ridge Regularization, Random Forest Regression and Support Vector Regression (SVR). <br>
**Of the three models, the Random Forest Regression model had the best performance as it has the best metrics with the lowest MAE, MSE and RMSE, and the highest R² score. The Random Forest Regression model was chosen as the final model.** <br>

- For chosen features (applied to final model, Random Forest Regression): features which deal with screen size and technical specifications (OS, CPU, GPU, RAM, Storage, etc.) were chosen as they could influence the price. <br>
- Cross-validation (with GridSearchCV) was used as a validation scheme. Cross-validation was used to evaluate the holdout data for the final model, and has similar results/metrics with the test data.<br>
- All three regression models required the data to be converted into numerical format hence the use of encoding. OneHotEncoder was used was used on all features (which were originally objects/strings) to convert their values to be numerical. <br>   
- With what was stated above, the final model (Random Forest Regression) had the encoding feature OneHotEncoder to convert the feature values to be numerical. This encoder was applied as part of feature engineering for the final model. <br>  
- Continuing with feature engineering, scaling was not applied on the data for the final model (Random Forest Regression), as it was not necessary for the Random Forest model. <br>
- As per prediction experimentation, with "new_data_df" (data frame)" as input, the Random Forest Regression Model was able to provide a prediction of the laptop price (in euros). <br>
- The final model was deployed as a joblib file (as 'M2P16_rfr_model.joblib'). After loading the final model, the final model ('M2P16_rfr_model.joblib') was able to make a prediction. <br>
