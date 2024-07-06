# Startup-Prediction

The goal of this project is to predict the success or failure of startups based on various features. This is a classification problem that involves both numerical and categorical data. By building a predictive model, we aim to provide valuable insights that can help stakeholders make informed decisions about potential startup investments.


## Objectives
**1. Data Understanding and Preprocessing**

- Import necessary libraries
- Load and explore the dataset
- Handle missing values
- Analyze numerical and categorical features
- Visualize the data for better understanding
- Feature Engineering and Selection

**2. Identify and handle outliers**
- Assess the importance of features
- Create new features if necessary
- Model Building and Evaluation

**3. Choose appropriate classification models**
- Train and validate models
- Evaluate model performance using suitable metrics
- Deployment and Insights

### 1. Import necessary libraries

First, we import all the necessary libraries required for our analysis and model building.

- Numpy and Pandas for numerical operations and data handling.
- Matplotlib and Seaborn for creating visualizations.

### Load and explore the dataset

Load the dataset into a Pandas DataFrame for easy manipulation and analysis.

### Handle Missing Values

Identifying features with missing values helps us understand the extent of missing data and informs our strategy for handling it.

Visualize missing data using missingno to see patterns and correlations between missing values, aiding in deciding which features to drop or impute.

Missing data is prevalent in several features of the dataset, with varying percentages:

- Age of company in years: 9.32%
- Internet Activity Score: 13.77%
- Short Description of company profile: 31.57%
- Industry of company: 26.27%
- Focus functions of company: 6.36%
- Investors: 29.66%
- Employee Count: 35.17%
- Employees count MoM change: 43.43%
- Has the team size grown: 10.59%
- Est. Founding Date: 23.09%
- Last Funding Date: 25.85%
- Last Funding Amount: 33.90%
- Country of company: 15.04%
- Continent of company: 15.04%
- Specialization of highest education: 20.55%
- Industry trend in investing: 17.37%
- Gartner hype cycle stage: 36.44%
- Time to maturity of technology (in years): 36.44%

**Visualizing the missing data using heatmap:**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/heatmap%20purple.png)

We can infer that fields such as

- **Internet Activity Score** - Important for this analysis

- **Investors** - Investor detail is not so important

- **Est. Founding Date** - Not sure if it is founding date or Funding date, so cannot conclude

- **Years of education** - Though it contains some missing values, it is very least

- **Disruptiveness of technology** - Contains least missing values

- **Time to maturity of Technology** - Since it is a Startup, we can roughly impute the missing values with mean years

- **Plotting Correlation matrix to view missing values using Missingno Library**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/correlation%20matrix%20missing%20values%20blue.png)

We can see that there exists more missing values for colors in dark blue for correlations.

Let us now visualize how different variables can be compared with the Dependent-Company Status: Success vs Failed

**1. Count of Success and Failed**
   
![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/1.%20Success%20vs%20failure%20countplot.png)

This graph shows the distribution of companies between "Success" and "Failed" statuses. 

There are approximately 300 successful companies compared to about 170 failed ones. 

This indicates a higher success rate overall, with roughly 64% of companies succeeding and 36% failing.

**2. Age of Company in years vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/2.%20age%20of%20company%20in%20years.png)

For successful companies, the vast majority (about 300) are 0 years old, while very few (less than 50) are 1 year old. 

For failed companies, there's a more even split, with about 125 being 0 years old and about 50 being 1 year old. 

This suggests that newer companies (0 years) have a higher success rate, but also a higher failure rate in absolute numbers.

**3. Internet Activity Score vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/3.%20internet%20activity%20score.png)

Companies with an Internet Activity Score of 0 are much more prevalent in both success and failure categories. 

For successful companies, about 280 have a score of 0, while only about 20 have a score of 1.

For failed companies, about 125 have a score of 0, and about 50 have a score of 1. 

This could indicate that having a higher Internet Activity Score (1) is associated with a higher likelihood of failure.

**4. Short Description of company profile vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/4.%20short%20description%20of%20company%20profile.png)

For successful companies, having no short description (score 0) is more common (about 225 companies) than having one (about 75 companies). 

For failed companies, the split is nearly even between having a description (score 1) and not having one (about 90 companies each). 

This suggests that having a short company description doesn't necessarily correlate with success.

**5. Industry of company vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/5.%20industry%20of%20company.png)

In both success and failure categories, companies with an industry score of 0 are more common. 

For successful companies, about 250 have a score of 0, while about 50 have a score of 1.

For failed companies, about 100 have a score of 0, and about 70 have a score of 1.

This might indicate that companies in certain industries (represented by score 0) tend to have higher success rates.

**6. Focus functions of company vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/6.%20focus%20functions%20of%20company.png)

The vast majority of both successful and failed companies have a focus function of 0.

This suggests that the focus function alone is not a strong predictor of success. 

However, there's a small portion of failed companies with focus function 1, which is almost absent in successful companies. 

This could indicate that focus function 1 might be associated with higher risk or challenges.

**7. Investors vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/7.%20Investors.png)

Successful companies show a much higher proportion of investor status 0 compared to 1, while failed companies have a more balanced distribution. 

This could suggest that:

- a) Companies with investor status 0 (possibly indicating self-funding or specific types of investors) might be more stable or have better financial management.

- b) Alternatively, successful companies might be less likely to need or seek certain types of investors (status 1).

**8. Employee Count vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/8.%20Employee%20count.png)

The pattern here is intriguing. Successful companies predominantly fall into category 0, while failed companies are more evenly split between 0 and 1, with a slight majority in 1. 

This could indicate that:

- a) Smaller team sizes (assuming 0 represents fewer employees) might be more efficient or adaptable.

- b) Rapid scaling of employee count might pose challenges that some companies fail to navigate successfully.

**9. Employees count MoM change**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/9.%20Employees%20count%20MoM%20change.png)

Successful companies show more stability (category 0), while failed companies have more volatility (category 1). This suggests that:

- a) Consistent, steady growth might be more sustainable than rapid fluctuations.

- b) Rapid month-over-month changes could indicate either unsustainable growth or desperate measures in failing companies.

**10. Has the team size grown vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/10.%20Has%20the%20team%20size%20grown.png)

Almost all successful companies fall into category 0 (no growth), while failed companies are split. 

This is counterintuitive and could mean:

- a) The timeframe matters - successful companies might have grown before the period measured and then stabilized.

- b) Efficiency and lean operations might be more important than team size growth.

- c) Growing team size might be a response to challenges in struggling companies, rather than a sign of success.

**11. Est. Founding Date vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/11.%20Founding%20date.png)

This plot shows that companies with an earlier founding date (0) tend to be more successful than those with a later founding date (1). 

This could suggest that established companies with more experience in the market have a higher chance of success.

**12. Last Funding Date vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/12.%20Last%20funding%20date.png)

Companies with a more recent last funding date (1) seem to have a lower success rate compared to those with an earlier last funding date (0). 

This might indicate that companies relying on recent funding are still in a precarious position, while those who haven't needed recent funding are more stable.

**13. Last Funding Amount vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/13.%20Last%20funding%20amount.png)

The distribution here is more even, but companies with lower last funding amounts (0) still show a higher success rate. 

This could imply that companies requiring less capital are more efficient or have a more sustainable business model.

**14. Country of Company vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/14.%20Country%20of%20company.png)

There's a significant difference in success rates based on the country (0 vs 1).

Companies from country 0 have a much higher success rate, suggesting that certain countries provide better environments for business success, possibly due to economic conditions, regulations, or market opportunities.

**15. Specialization of highest education vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/16.%20Specialization%20of%20highest%20education.png)

Companies with specialization 0 are much more likely to succeed than fail, while those with specialization 1 have a more balanced outcome. 

This implies that a particular type of educational background (represented by 0) may be more advantageous for company success.

**16. Industry trend in investing vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/17.%20Industry%20trend%20in%20investing.png)

The pattern indicates that industry trend 0 is strongly correlated with success, while trend 1 has more balanced outcomes.

**17. Gartner hype cycle stage vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/18.%20Gartner%20hype%20cycle%20stage.png)

Stage 0 is associated with more successes, while stage 1 has more failures. 

This suggests that the company's position in the hype cycle significantly impacts its chances of success.

**18. Time to maturity of technology (in years) vs Success and Failed**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/19.%20Time%20to%20maturity%20of%20company%20(in%20years).png) 

Technology maturity category 0 is linked to more successes, while category 1 shows more failures. 

This implies that the maturity timeline of a company's technology is a crucial factor in its success.


## Data Preprocessing 

Features with high missing values were dropped, and important features were imputed with suitable values. 

Features that are highly correlated or dependent on each other were also identified for removal to improve model performance.

### Feature Removal

I removed several features from the dataset due to a high proportion of missing values or potential redundancy. This step helps to improve the model's performance and reduce noise in the data.

Removed Features:

- 'Employees count MoM change'
- 'Gartner hype cycle stage'
- 'Time to maturity of technology (in years)'
- 'Employee Count'
- 'Last Funding Amount'
- 'Short Description of company profile'
- 'Investors'
- 'Industry of company'
- 'Last Funding Date'
- 'Est. Founding Date'
- 'Specialization of highest education'

These features were dropped using pandas' drop() function with axis=1 to remove columns.

**Why?**

- Some features may have had a high percentage of missing values, making them less reliable for analysis.

- Others might have been too specific or potentially redundant, not contributing significantly to the model's predictive power.

- Removing these features helps to simplify the model and potentially improve its generalization ability.

Let us again check for Null values in our dataset using the heatmap I used before:

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/101.%20checking%20null%20values%20again.png)

### Handling Correlated and Dependent Variables

**What are Correlated Variables?**

Correlated variables are features that exhibit a statistical relationship with each other. High correlation between variables means that one variable can be linearly predicted from the other with a certain degree of accuracy. In the context of machine learning, multicollinearity (high correlation between independent variables) can lead to several issues:

- **Redundancy:** Correlated variables provide redundant information, which can inflate the importance of certain features.

- **Model Stability:** High correlation can make the model coefficients unstable and sensitive to small changes in the data.

- **Interpretability:** It becomes challenging to interpret the individual impact of correlated features on the target variable.

**What are Dependent Variables?**

Dependent variables, in the context of feature selection, refer to those that are directly or indirectly dependent on other features, leading to potential redundancy in information. In machine learning, ensuring independence between features helps in creating a more generalizable and robust model.

**Why Avoid Correlated Variables?**

Avoiding correlated variables is crucial for the following reasons:

- **Model Accuracy:** Reducing multicollinearity improves the accuracy of the model by ensuring that each feature contributes unique information.

- **Coefficient Interpretability:** It makes the coefficients of the model more interpretable by isolating the effect of each feature on the target variable.

- **Performance:** It enhances the performance and stability of the model, making it less sensitive to variations in the data.

**Features Removed Due to Correlation**

In this project, the following features were removed due to high correlation or dependency with other variables:

- **success_fail:** This target variable was removed from the feature set to prevent data leakage and ensure proper model training.

- **Have been part of successful startups in the past?:** This feature was highly correlated with the target variable (success_fail) and was removed to reduce redundancy and improve model stability.

### Analysing Numerical Features

**Boxplot: y = 'Industry trend in investing', x = 'success_fail'**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/102.%20industry%20trend%20vs%20success%20failure.png)

- Shows distribution of data for two groups (0 and 1)
- Group 1 has a higher median and wider range of values
- Some outliers present in both groups

**Boxplot: x = 'Industry trend in investing', y = 'Exposure across the globe', hue = 'success_fail'** 

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/103.%20exposure%20across%20globe.png)

- Compares success rates across different "Industry trend in investing" values
- Success rate (blue) generally increases as the industry trend value increases
- At higher trend values (3.0-5.0), success rates are consistently above 70%

**Distplot: 'Industry trend in investing'**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/104.%20dist%20plot.png)

- Displays distribution of "Industry trend in investing" values
- Multi-modal distribution with peaks around 0, 2, and 3-4
- Highest density occurs around 3-4 on the x-axis

**Countplot: x= 'Highest education'**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/105.%20count%20plot%20-%20highest%20ed.png)

- Shows count of individuals by highest education level
- Bachelors degrees are most common, followed closely by Masters
- PhD holders are the smallest group
- "0" category (possibly indicating no degree) has a significant count

**Boxplot: y = 'Internet Activity Score', x = 'success_fail'**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/106.%20box%20plot%20internet%20activity%20score.png)

- Compares distribution of "Internal Activity Score" for two groups (0 and 1)
- Group 1 has a much higher median score and larger range
- Both groups have numerous outliers, especially on the upper end
- Group 0 has a more compact interquartile range

**Boxplot: y = 'Internet Activity Score', x = 'success_fail', hue = 'Highest education'**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/107.%20box%20plot%20internet%20act%20score%20vs%20educ.%20vs%20sucess%20failure%20vs%20.png)

- There appears to be a correlation between higher education levels and success.
- PhD and Masters degree holders generally show higher scores compared to Bachelors and other degree holders.
- However, there is significant overlap in the score distributions across education levels.

# Startup Success Prediction Model

This section of the notebook focuses on implementing and evaluating various machine learning models to predict the success or failure of startups based on preprocessed numerical and categorical features.

## Model Implementation and Evaluation

### 1. Logistic Regression

Logistic Regression is used as a baseline model due to its simplicity and interpretability.

**Why it's used:**

- Provides a good baseline for binary classification problems

- Offers easily interpretable results, showing the impact of each feature on the prediction

- Works well when there's a linear relationship between features and the log-odds of the outcome




### Decision Tree Classifier

Decision Trees are used to capture non-linear relationships and feature interactions.

**Why it's used:**

- Can capture complex, non-linear relationships in the data

- Provides feature importance rankings

- Handles both numerical and categorical data well

- Results are easily visualizable and interpretable



### Random Forest Classifier

Random Forest is an ensemble method that builds upon Decision Trees to create a more robust model.

**Why it's used:**

- Reduces overfitting compared to individual decision trees

- Handles high-dimensional data well

- Provides feature importance rankings

- Often achieves high accuracy in various domains

### Model Comparison and Selection

**Comparison Metrics:**

- Accuracy: Overall correctness of the model

- Precision: Ability to avoid labeling negative instances as positive

- Recall: Ability to find all positive instances

- F1-score: Harmonic mean of precision and recall

- ROC-AUC: Model's ability to distinguish between classes

### Selection Criteria:

- Choose the model with the best overall performance

- Consider trade-offs between accuracy and interpretability

- Factor in computational efficiency for deployment scenarios

### Hyperparameter Tuning

For the best performing model(s), conduct hyperparameter tuning using Grid Search 

### Final Model Evaluation

- Retrain the best model with optimal hyperparameters on the entire training set

- Evaluate on the held-out test set for an unbiased estimate of performance

- Generate a comprehensive classification report and confusion matrix

### Model Interpretation

- For Logistic Regression: Analyze coefficients

- For Tree-based models: Visualize feature importances

- Use SHAP (SHapley Additive exPlanations) values for more detailed feature impact analysis

