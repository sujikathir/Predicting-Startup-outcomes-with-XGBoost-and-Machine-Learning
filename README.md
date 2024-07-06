# Startup-Prediction

The goal of this project is to predict the success or failure of startups based on various features. This is a classification problem that involves both numerical and categorical data. By building a predictive model, we aim to provide valuable insights that can help stakeholders make informed decisions about potential startup investments.


## Objectives
1. Data Understanding and Preprocessing

- Import necessary libraries
- Load and explore the dataset
- Handle missing values
- Analyze numerical and categorical features
- Visualize the data for better understanding
- Feature Engineering and Selection

2. Identify and handle outliers
- Assess the importance of features
- Create new features if necessary
- Model Building and Evaluation

3. Choose appropriate classification models
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

**Plotting Correlation matrix to view missing values using Missingno Library**

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/correlation%20matrix%20missing%20values%20blue.png)

We can see that there exists more missing values for colors in dark blue for correlations.

Let us now visualize how different variables can be compared with the Dependent-Company Status: Success vs Failed

1. Count of Success and Failed
   
![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/1.%20Success%20vs%20failure%20countplot.png)

2. Age of Company in years vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/2.%20age%20of%20company%20in%20years.png)

3. Internet Activity Score vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/3.%20internet%20activity%20score.png)

4. Short Description of company profile vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/4.%20short%20description%20of%20company%20profile.png)

5. Industry of company vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/5.%20industry%20of%20company.png)

6. Focus functions of company vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/6.%20focus%20functions%20of%20company.png)

7. Investors vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/7.%20Investors.png_

8. Employee Count vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/8.%20Employee%20count.png)

9. Employees count MoM change

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/9.%20Employees%20count%20MoM%20change.png)

10. Has the team size grown vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/10.%20Has%20the%20team%20size%20grown.png)

11. Est. Founding Date vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/11.%20Founding%20date.png)

12. Last Funding Date vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/12.%20Last%20funding%20date.png)

13. Last Funding Amount vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/13.%20Last%20funding%20amount.png)

14. Country of Company vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/14.%20Country%20of%20company.png)

15. Specialization of highest education vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/16.%20Specialization%20of%20highest%20education.png)

16. Industry trend in investing vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/17.%20Industry%20trend%20in%20investing.png)

17. Gartner hype cycle stage vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/18.%20Gartner%20hype%20cycle%20stage.png)

18. Time to maturity of technology (in years) vs Success and Failed

![](https://github.com/sujikathir/Startup-Prediction/blob/main/images/19.%20Time%20to%20maturity%20of%20company%20(in%20years).png) 

