# ADIDAS SALES PROJECT 
## PART ONE: Residual Analysis

## Introduction
This dataset is An Adidas sales dataset that have information on the sales of Adidas products, number of units sold, the total sales revenue, the location of the sales, the sales outlets and method of sales.
This dataset is very granular, each row represents a line item for a purchase at one of 6 Retailers outlet spread across all the states in the five Region of USA. there is no missing value in this dataset. this project has three part to it, part one seeks to answer project statement using *Residual analysis* and part two seeks to use *Dummy variables in regression* to explain the project statement and part three, I want to give Adidas data insight on how not to over dependent on their best performing product using the *decision tree algorithm* to address this business problem.  

## Data Source
The data used in this analysis is available publicly on Kaggle.com. <https://www.kaggle.com/datasets/heemalichaudhari/adidas-sales-dataset>

## Project Statement:
"How are quarterly sales affected by quarter of the year, region, and by product?
## Steps Followed
*  Load the Libraries
## Descriptive Analysis
*  Data Preparation (ETL)
## Exploratory Analysis
*  Statistical Analysis

# Insight
![Regression Opreation_profit On units_sold With A Scatter Plot](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/8ff36b45-8aff-452c-9a12-9be0e858c25b)
![Residual Table ](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/2279c600-6ca1-445c-83a0-9e23d5582339)
![Best Performing Store and Quater of the year](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/7780f757-0786-4dce-bc2e-2c046a9e2263)
![[Best Performing Store and Quater of the yea](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/eef87407-8c91-4a27-9b89-1f8eef82bf24)

# Residual Analysis Explaining the project statement
*  Best stores are Walmart and Sports Direct, best product is Women's Apparel
   The store at Southeast beat their goal during second and third quarters for 2021 by at least $198,601.2
   The store at South also beat its expectation during third and fort quarter by at least $154,993.3.
*  Worst stores are West Gear and Sports Direct in the West and South for Men's Athletic Footwear and Men's Street Footwear.
   The store at West missed its expected quarterly oprating_profit for first quarters of 2021 by at least $108,757.6.
   The store in the South also missed its expected quarterly oprating_profits for third quarter in 2021 by about $102,934.7.

   # Recommendation
   The manager, may want to look into the two stores that under performed during 2021 to work on improving their performance. In contrast, He may want to look into the two stores that outperformed during 2021 to find out if their best practices can be replicated in other locations.


# ADIDAS SALES PROJECT 
# PART TWO: Dummy Variables In Regression

## Project Statement:
"How are quarterly sales affected by quarter of the year, region, and by product?

# Qualitative Variables
I Used Qualitative variable quarter of the year because machine learning algorithms, including regression, rely on numeric values. So we have to convert qualitative variables to numeric variables.

# Dummy Variables
What is often done is a series of binary variables is used to capture the different levels of the qualitative variable. Specifically, we would replace the quarter of the year variable, quarter_NoYear, with three variables: Second, Third, and Fourth. The values in these columns take on a value of 1 if the observation fits into that category, and a value of zero otherwise. We only need three columns because if they all have a value of 0, then that means the observation fits into the first quarter.
Here's a dataframe to illustrate that idea with a bit more detail:

data.frame('quarter_char' = c('First', 'Second', 'Third', 'Fourth'),
                 'quarterSecond' = c(0, 1, 0, 0),
                 'quarterThird' = c(0, 0, 1, 0),
                 'quarterFourth' = c(0, 0, 0, 1))
                 
![ Relationship between operating_profit on quarter_char column](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/18a2082c-af65-45cf-b2ce-a44525066473)
There is a coefficient estimate for the second through fourth quarters, but not for the first quarter. The intercept represents the estimate of operating_profit for the first quarter, and the coefficient estimates for the other variables represent the difference between that quarter from the first quarter. the operating_profit for third quarter is 13,142 higher than the baseline estimated and 7,779 higher than the baseline estimated in second quarter.

# The Unique Effect of Quarter of the Year
Quarter of the year may have a significant effect on quarterly oprating_profit after controlling for the percentage of sales that come from other products. Let's test this out by including it with the unit_sold variables that we have already investigated
![image](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/1256b558-24d6-421c-a6c6-a457e3c27644)

# Insight

regression analysis with the addition of the "units_sold" variable yields the following results:

The coefficient for the "units_sold" variable is 226.424 with a standard error of 1.152. This means that for each additional unit sold, the operating profit is estimated to increase by 226.424. The coefficient is highly significant (p-value < 0.001), indicating a strong positive relationship between units sold and operating profit.

The coefficient for the "quarter_charFourth" variable is 11,268.915 with a standard error of 696.438. This coefficient represents the difference in operating profit between the fourth quarter and the baseline quarter, while holding the number of units sold constant. The positive coefficient suggests that the fourth quarter tends to have higher operating profit compared to the baseline quarter.

All coefficients are highly significant (p-values < 0.001), indicating their strong relationship with operating profit.

The multiple R-squared value is 0.8019, indicating that the model with "units_sold" and quarterly variables explains approximately 80.19% of the variability in operating profit. The adjusted R-squared value is 0.8018, which takes into account the number of predictors in the model.

The F-statistic is 9756 with a p-value < 2.2e-16, indicating that the overall model is highly significant.
This change is effectively communicated by visualizing the coefficients from all three models.
![coefficients from all three models](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/373776f0-51a6-48f0-a8ed-9d0eb974da83)

# Conclusion
Based on Model 2 and Model 3, it appears that the quarter_charThird variable had the largest positive coefficient and was statistically significant in both models. This suggests that the third quarter (quarter_charThird) had the most significant positive impact on the dependent variable compared to the other quarters (quarter_charFourth and quarter_charSecond). However, the practical significance and implications may vary depending on the specific situation or domain being studied.

# ADIDAS SALES PROJECT 
# PART THREE: Decision Tree Algorithm

# Introduction:

This analysis is squeal my work tittled *Residual Analysis: How Adidas Quarterly Sales Are Affected By Quarter Of The year, Region, And By Product* As an analyst, I want to give Adidas data insight on how not to over dependent on their best performing product. I will now use the decision tree algorithm to address this business problem. 
I assumed Adidas is planning for the future and would like to set up their business so they are not so reliant on selling their best product: Women's Apparel. One way to do that is to increase the sales of profitable products. Thus, Adidas would like to predict when a transaction is a going to be a sale of a high margin profit product. Profit margin is the percentage of gross profit to revenue, or revenue minus costs divided by revenue. It is a percentage of how much profit each product makes or what percentage of profit is earned for each dollar of revenue. I have to create the target veriable 'column' from 'Opreating_Margin' 

# Data Preperation

```{r}
library(caret)

# Assuming you have a data frame called Adidas_tree_filtered
# and the target variable is "Op_Margin"

set.seed(121)  # Set a seed for reproducibility
index <- createDataPartition(Adidas_tree_filtered$Op_Margin, p = 0.75, list = FALSE)

train_data <- Adidas_tree_filtered[index, ]  # Training data
test_data <- Adidas_tree_filtered[-index, ]  # Testing data
```
I ran the model to find its accuracy 
Overall, our model does a great job at predicting when a purchase will be high profit margin versus low profit margin and gets it right 74% of the time. The aspect of the model that is the least effective is its sensitivity and the aspect that is the most effective is the specificity. This means that the model is very good at classifying the low margin purchases successfully (specificity), but slightly worse at classifying the high margin purchases correctly (sensitivity). Thus, while the model is quite good overall, it particularly excels at identifying bad transactions. As we examine the tree below, it should become clear why low margin products are a bit easier to classify.

# Insight 
I examine the details of the tree I have created and what it might tell me that might help Adidas increase their sales of profitable products. I started this process very simply by using the `summary()` function on the tree object, `model_tree`. I learn a couple very useful things here. First, we learn that only three variables were used in our tree--`Operating_Profit` `Product` and `Total_Sales`. Next, we are told how many terminal nodes exist. Finally, we are given some error measurements. Residual mean deviance is a measure of variance in the model and misclassification error rate is measure of how many examples were misclassified. It shows that 1,875, or about 26%, of our total observations were incorrectly classified (split into the wrong partition). 
# Summarize the results from our model
```{r}
summary(model_tree1)
```
Classification tree:
tree(formula = Op_Margin ~ ., data = train_data)
Variables actually used in tree construction:
[1] "Total_Sales"      "Product"          "Operating_Profit"
Number of terminal nodes:  4 
Residual mean deviance:  1.103 = 7970 / 7229 
Misclassification error rate: 0.2592 = 1875 / 7233 
To Understand this result, let plot the Tree in text form and in graphe

# Tree in text form
```{r}
model_tree1
```
node), split, n, deviance, yval, (yprob)
      * denotes terminal node

 1) root 7233 9425.0 high ( 0.6433 0.3567 )  
   2) Total_Sales < 22477 4305 4303.0 high ( 0.8005 0.1995 ) *
   3) Total_Sales > 22477 2928 3968.0 low ( 0.4122 0.5878 )  
     6) Product: Men's Street Footwear,Women's Apparel 959 1291.0 high ( 0.5996 0.4004 )  
      12) Operating_Profit < 149813 733 1015.0 high ( 0.5184 0.4816 ) *
      13) Operating_Profit > 149813 226  180.7 high ( 0.8628 0.1372 ) *
     7) Product: Men's Apparel,Men's Athletic Footwear,Women's Athletic Footwear,Women's Street Footwear 1969 2471.0 low ( 0.3210 0.6790 ) *

![Decision Tree](https://github.com/akpatiudo/Adidas-Sales-Project/assets/118566096/260e2845-5f2a-4d9e-94a0-94a3d5ce922a)

So, what do we learn from the text above and the plot? As we move through the tree, moving to the left is "No" while moving to the right is "Yes". "high" and "low" at the leaf nodes indicates that is the prediction of the profitability of the purchase. 
We actually learn a lot that can help Adidas. The first, and most significant split that determines whether a purchase will be for a high or low magin profit is whether the purchases Men's Apparel,Men's Athletic Footwear,Women's Athletic Footwear,Women's Street Footwear or Men's Street Footwear,Women's Apparel. If the answer to this is yes, we move to the right of the tree and the product is very likely to be low profitability. While the management team at Adidas surely knows which products are high and low profit. For Men's Street Footwear, Women's Apparel, profitability is also predicted to be high, whether Opreating_profits is above or below $149,813.




