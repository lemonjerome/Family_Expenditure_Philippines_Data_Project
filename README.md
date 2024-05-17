# Family_Expenditure_Philippines_Data_Project

This project is a **Machine Learning** project that uses a linaer regression model to predict the total household expenditure of a family in the Philippines. The main libraries used were pandas for tabular data exploration and cleaning, matplotlib, plotly, and seaborn for visualizations, and scikit-learn for machine learning.

## Data Selection and Preparation

The dataset used in this project is from https://www.kaggle.com/datasets/grosvenpaul/family-income-and-expenditure. The column names were adusted such that all characters are in lower case, all the spaces were replaced with '\_', and all the '/' were replaced with 'or'.

The following are the features of the dataset:

- total_household_income
- region
- staple_food_expenditure
- source_of_income
- agricultural_household_indicator
- meat_expenditure
- seafood_expenditure
- leisure_expenditure
- alcohol*expenditure*
- tobacco_expenditure
- medical_expenditure
- transportation_expenditure
- communication_expenditure
- utilities_expenditure
- housing_tax
- education_expenditure
- crop_farming_expenditure
- household_head_gender
- household_head_age
- household_head_marital_status
- household_head_highest_grade_completed
- education_rank
- household_head_job_indicator
- household_head_occupation
- household_head_class_of_worker
- occupation_group
- type_of_household
- total_number_of_family_members
- members_with_age_less_than_5_year_old
- members_with_age_5_to_17_years_old
- total_number_of_family_members_employed
- house_floor_area
- house_age
- number_of_bedrooms
- tenure_status
- electricity
- main_source_of_water_supply
- number_of_television
- number_of_cd_or_vcd_or_dvd
- number_of_component_or_stereo_set
- number_of_refrigerator_or_freezer
- number_of_washing_machine
- number_of_airconditioner
- number_of_car_or_jeep_or_van
- number_of_landline_or_wireless_telephones
- number_of_cellular_phone
- number_of_personal_computer
- number_of_stove_with_oven_or_gas_range
- number_of_motorized_banca
- number_of_motorcycle_or_tricycle

To get the total expenditure in one row, all the columns with expenditure and tax were added and the result was then stored in a new column 'total_expenditure'.

## Data Exploration

The distribution of some features were visualized to get an idea of the dataset being worked with. The features that were chosen were age of household head, number of family members, the houshold head marital status, total income, and toal expenditure. Plotly was used to plot a histogram and a boxplot of the features.

### Age

<insert pics>

The visualization suggests a normally distibuted dataset in terms of household head age. The min nand max values of 9 and 99, respectively, are alarming. If these are not erros in the data collection, the government may consider looking into these issues. The histogram is also colored according to the gender of the household head. We can see that there are more male breadwinners than females.

### Number of Family Members

<insert pics>

The histogram shows a right-skewed distribution which is supported by a boxplot with a longer right whisker and multiple outliers on the right. The mean number of the family members is 4 but the can reach to more than 20 members

### Marital Status

<insert pics>

There are only four possible classifications: single, widowed, married, divorced. The classification with the highest count is married. The plots are also colored according to gender, and married household heads are mostly male. The distribution of gender in single and divorced heads is fairly even while there are heads that are widowed is mostly female.

### Total Income

<inset pics>

The distribution is heavily skewed to the right. This is supported by a huge difference in the median and mean where the mean is significantly higher than the median. The boxplot also shows many outliers that may have shifted the mean to the right.

### Total Expenditure

<inset pics>

The shape of the curve of the total expenditure is similar and almost identical to that of the total income. This may suggest a possible correlation between the two features.

## Base Model

The base model only used non-categorical features. The features with 'expenditure' and 'tax' were excluded from the linear regression model because it has a direct causal relationship with the target variable. The correlation of each feature with the target 'total_expenditure' was observed, and only the ones with a coeffcient of 0.3 or higher was chosen, meaning the model only included features with moderate to high correlation with the target.

The following are the features (with their corresponding correlation coefficients) that are included as the inuts of the base model:

- total_household_income                       0.709464
- house_floor_area                             0.396777
- number_of_television                         0.478091
- number_of_cd_or_vcd_or_dvd                   0.352845
- number_of_component_or_stereo_set            0.320662
- number_of_refrigerator_or_freezer            0.473549
- number_of_washing_machine                    0.451621
- number_of_airconditioner                     0.553453
- number_of_car_or_jeep_or_van                 0.529115
- number_of_landline_or_wireless_telephones    0.364719
- number_of_cellular_phone                     0.465335
- number_of_personal_computer                  0.517076
- number_of_stove_with_oven_or_gas_range       0.365671
- number_of_bedrooms                           0.425846

Inputs and targets were fit into a linear regression model using sci-kit learn. Predictions were made using the same inputs. The loss of the model was measured using a root mean squared error (rmse). 

The rmse for this model is 1575.0370982314587. The range of total-expenditure for the regular or non-outlier data points is 70 Pesos to 6836 Pesos. The loss is too high. Looking at the scatter plots plots of total_houseghold_income (0.709464), number_of_airconditioner (0.553453), 

Looking at the Pictures

## Model Improvements/Training

