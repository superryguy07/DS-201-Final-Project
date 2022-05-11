# State Spending and Test Score Quality

##### By Ryan Wedeking, Nate Bontje, and Rhys Yochem

This contains a summary of the Final Project for DS 201. For more in-depth insight, please check out our walk-through video or run the notebook below in RStudio.

## Business Understanding

The United States is a uniquely diverse country in which peoples from all backgrounds and cultures reside. There are unfortunate disparities between these groups, whether it be based on region of origin, race, gender, sexual orientation, religion, socioeconomic status or other. One aspect of society in which these differences become apparent, is within the public education system.

In addition to measuring academic progress from Kindergarten to the end of high school, standardized test services collect data regarding the different demographics of those who take their test. This helps to provide them actionable insight into what factors impact the quality of education in those who are taking their tests. Then, the scores on the standardized tests are used to inform government decisions regarding funding to different states and districts in the hopes of providing more resources to schools that are under performing.

We have been tasked with analyzing data regarding test scores, funding and expenditures in different states, and population characteristics in an effort to gain actionable insight into what factors are related to student performance on the NAEP, which is a standardized test developed by the Educational Testing Service that aims to measure academic progress from K-12.

## Data Understanding

The data set we used for this major undertaking takes data from a number of sources and compiles them into one data set for ease of analysis. We acknowledge and appreciate that the data set was compiled by Roy Garrard and then posted for public use on Kaggle.com, a website designed for collaboration in the data science community.

In compiling the data, Mr. Garrard acquired publicly available data from NCES (National Center for Educational Statistics) regarding educational statistics, and data from the US Census regarding the funding and expenditures for education in different states. He then used his own python code to compile the data into a single spreadsheet that he uploaded to Kaggle that we then downloaded for our own use in the following analysis.

In the initial data set, there are 25 variables present, however, we did not use every feature in our analysis. The following table gives a brief overview of the variables used:

| Feature                      | Description                                               |
|------------------------------|-----------------------------------------------------------|
| State                        | US state data originates from                             |
| Year                         | Year data was collected                                   |
| Enroll                       | Count for enrolled students in the state                  |
| Total Revenue                | Total amount of revenue for state                         |
| Federal Revenue              | Amount of revenue from federal government                 |
| State Revenue                | Amount of revenue from state government                   |
| Local Revenue                | Amount of revenue at local level                          |
| Total Expenditure            | Total Expenditure for the state                           |
| Instruction Expenditure      | Expenditure towards teacher salaries and school materials |
| Support Services Expenditure | Expenditure towards student support services              |
| Capital Outlay Expenditure   | Expenditure towards equipment and equipment improvement   |
| Other Expenditure            | Miscellaneous expenditures                                |
| Average Math 4 Score         | Average 4th grade NAEP math score (out of 500)            |
| Average Math 8 Score         | Average 8th grade NAEP math score (out of 500)            |
| Average Reading 4 Score      | Average 4th grade NAEP reading score (out of 500)         |
| Average Reading 8 Score      | Average 8th grade NAEP reading score (out of 500)         |

The data contains data from states in United States of America spanning from 1986-2019. The dataset contains a number of incomplete feature data in varying places across the dataset. For this reason, we decided to focus our analysis on the year 2015, as it was the most recent year containing complete data for analysis purposes.

## Data Preparation

To get more accurate numbers, we deemed it necessary to get the amount of money spend in each of the categories per enrolled student, as larger states would theoretically have to spend more money to get the same result as smaller states because they have more students to take care of. To do this, we appended our table to include 5 new columns which included numbers for the total spending of the state divided by the reported number of enrolled students. These new variables will be the main focus of our investigation instead of raw numbers.

| Feature                       | Description                                                           |
|-------------------------------|-----------------------------------------------------------------------|
| ExpendTotalPerEnroll          | Total Government Expenditure Per Student Enrolled                     |
| ExpendInstructionPerEnroll    | Total Instruction Expenditure Per Student Enrolled                    |
| ExpendSocialServicesPerEnroll | Total Social Services Expenditure Per Student Enrolled                |
| ExpendOtherPerEnroll          | Total Expenditure on Uncategorized use Per Student Enrolled           |
| ExpendCapitalOutlayPerEnroll  | Total Spending on Equipment and Equipment Upkeep Per Student Enrolled |

## Modeling and Evaluating

### Exploratory Data Analysis

#### Confusion Matrix

When looking at the data available to us, we decided the best course of action to start would be a confusion matrix to see if there were any variables that correlated with the average reading or math scores of 8th graders on the exam. As you can see, the money spent per enrolled student in each state had a small correlation when it came to academic achievement. As such, we decided to graph each variable in relation to math and reading scores to see if there was a reason for these low correlations.

#### **![](https://lh5.googleusercontent.com/3d8-YzH9eVwt2YvahzZwcwUE_C_oSF-LJ41aKIR84BNkF7qRfiZSUs07AAPn2KGC6AdwAMbRQ2J9dwpw-5cZ53W36BQJiq2WwLDSVZgz7bMdvZMN-e7tHIuMIntJUrldvrG1NocnjgIrrg4BcA)**

#### Scatter Plots

Below are scatter plots comparing total expense, investment expense, social services expense, other expenses, and capital outlay expenses, all per student enrolled, compared to average reading and math scores. One outlier the we saw in every scatter plot was the district of Columbia, which was the lowest scorer in 2015 while spending by far the highest amount.

#### ![](https://lh5.googleusercontent.com/38LOIFRb81xY-0nK0VZpLRnnAiWQqIpf1YuDicMGr3xwCaYxoogvKtHaRjU3c7bh4mDk8K6SP2JihQaiRjuqJUfRl1K1JnCxOTw9QW8QhGIe3q2sCXXoGWmT8_6uag9U8HLdcVnNGX6R1XiZtg)

![](https://lh3.googleusercontent.com/iIW0Gom2WLm5S9nngcar0NFPNxsMfuc68w34Qz9JXYKnCuFeoW7DRBGoj12JCqIbWuOUQxAhkwNLyfyRCO9UA69L3RPfhsohe4sRYN2iipFLXwaq_wGz_mmgGiIeV1972hmKN_N76pXXR9lOng)

![](https://lh5.googleusercontent.com/kJrMAv73H_l6ef0z5mGNo-0jNPbgyxfdDY8cnYo1JF7kgU1ORsTpPJENxzzTk3hBuqfFwKFSrQPI97su1H3lHGS1_mW3QmMtQ0FEpCWMsZfmVENqB86T3jNI_THXgK67fbEDNARdtJKOElPFjg)

![](https://lh5.googleusercontent.com/mQ9DmihXuVhblImengGIsaBroKEKaRhEwOKAQQFBU15PkPDmNb8IfZnC8qLvY9FbxkYY7kkUHrRebM3ukl8TByp8IwyJU4ZaBpz45cLVxfUpOMdX0Diw9J0kyE1h4vOBRn5YKgaqnMDRGnJqaw)

![](https://lh5.googleusercontent.com/yCl5fhiv4_FYhamt_RzCMfWwXCKIEvWAkjYra5r8tnzsQSYbIyfuDmsv-Fyl08meVR1_wbF8opqCfomBREUDGHtxhT90nDhW1uzmPxsLYjo7UcO27um5d89biE5J6UX62PsLKbZ4X3FpPcYTxQ)

![](https://lh4.googleusercontent.com/w6cT98_vKv4245BMQUiPA_LPwpjsRpKUpVdNBuFLdv-p2n2wtLRwxiypamWYBRAwPOZaBSAw4YhcBU_-ABU_9Z8DjW57AXLrB1AXbwwk1az8HuB3dsuPCPeRq7qMhEpgcjqZ9NLMBZKRbESCnA)

![](https://lh4.googleusercontent.com/Ai5TEAW99ZKT4NouK8cWcwEuZrpmrNRxavm64AAsUTTIV_Nha9ugdcj93YyAdl_pK3HXFMcWPZuZXJyEfyoeY_C0isWsaxjGuRalWz5kuMz2wcMCCzHir5F5ER-Zs2kKaLeCI80hEWyyRBmr5g)

![](https://lh4.googleusercontent.com/eb3eBwFLxpRg3iVAJqWCN7LW7ZyDZCfp6gPnytsQeeV1iSBi3J-MjHCJcmtgQ12DLIa9x-Ed54A6FKHRMYTSmqKiaRFnafnU1mDF-f2Z1YRJNbGMks_6oYeLCA2JVHMtgTdnEU_rauVTjR7a0A)

![](https://lh6.googleusercontent.com/sEKeuT4oZbI1IaH_LTOo5qycdEzwQc19G9LD1A7v3gohrWmw7PYY35XXWbuQ7EAZxPOmZ0iY2Zw-ni97-l9G7cOChTBxdYVa_cvLQYWyz7bevbjnUyi07hmPBDvtKOYwsDibho1EK0XrluzaBA)

![](https://lh5.googleusercontent.com/WGd2ypXzex6BubakbJT9O-ywmnrzlQDCF0LvAp4zOMe4N6udkLjxA5pNy-EZfL2gEEsas-BJ28XUKuDT-YMyOQ_R4LHY8MLYa_Ru079XIwvHtfloUh1XeKl9bXVS6NXAXaZKfEAb62901Bi5-A)

### Second Confusion Matrix

After looking at the scatter plots, it became clear that there was no obvious general trend that showed increased or decreased spending lead to higher academic achievement as measured by the exam. But, by looking at the scatter plot, it became clear the District of Columbia was a significant outlier consistently. It became evident that the District of Columbia was confounding our results, and that the data itself would not be useful when trying to predict state spending as the total spending without proportions for amount enrolled is insignificant compared to states and the amount enrolled is as well. Because of this, we decided to remove the outlier as it was not pertinent to our research question or helpful in creating a model. As a result, we created a second confusion matrix to see how much the correlations changed after removing the variable.

![](https://lh5.googleusercontent.com/zjegeMf8bVYvfuJsCIm9j3RTdz2wVPiAnUjas4ByckAgHtiAZVBnGKkfhCajpRSZlP4tVy9PNyOaLjh8jhFRFO22lX5WwkkW-DsUANKncPSIRlxeUPkPq-yo-SnkdMzqfPfYRpNZN0NgJ79HqQ)

### Modeling

Following this exploratory data analysis, we decided to make a multivariate linear regression model to use the expenditure feature data to predict average grade 8 math scores. It is our hope that this model can be used to inform future funding and expenditure decisions in school districts to more effectively and efficiently use their resources to improve test performance. The model was created using the linear model function in R. The model was then trained using 70% of the data set and later tested using 30% of the data set that the model was not yet exposed to as a testing set. Lastly, the model was created using the data that excludes the District of Columbia as that was a consistent outlier in our data.

The code for creating and testing this model is shown below:

```{r}
options(warn=-1)

#Deleting District of Columbia
MyDataApend <- MyDataApend[-c(9), ]
set.seed(1234) #set seed for reproducibility

#splitting data into training and testing set
split1=sample(c(rep(0,0.7*nrow(MyDataApend)),rep(1,0.3*nrow(MyDataApend))))
train=MyDataApend[split1==0,]
test=MyDataApend[split1==1,]

#creating the model
Expendmod=lm(train$AVG_MATH_8_SCORE~train$INSTRUCTION_EXPENDITURE+train$SUPPORT_SERVICES_EXPENDITURE+train$OTHER_EXPENDITURE+train$CAPITAL_OUTLAY_EXPENDITURE)

#printing summary of model
summary(Expendmod)

#testing model 
predict=predict(Expendmod,test)
modelEval <- cbind(test$AVG_MATH_8_SCORE, predict)
colnames(modelEval) <- c('Actual', 'Predicted')
modelEval <- as.data.frame(modelEval)

#calculating performance metrics for model
mse <- mean((modelEval$Actual - modelEval$Predicted)^2)
rmse <- sqrt(mse)
rmse

#plotting residuals 
par(mfrow=c(2,2))
plot(Expendmod)
```

\
Looking at the residual plots and the root mean squared error from our model, we find that the model is not particularly accurate or effective in using the different expenditure variables to predict average 8th grade NAEP math scores.

## Deployment and Future Directions

As mentioned above, we found that the multivariate linear model approach was not an effective way to predict average math scores. The residual plots indicate that the normality distributions for our variables cannot necessarily be assumed and there are several other outliers in our data that are impacting the model performance (even though we removed the District of Columbia outlier). Thus, future improvements to the model should look into a different approach for predicting average NAEP scores. This could mean through transformations of our x variables, taking a non-linear approach, or switching to a classification approach where we use a logarithmic regression to predict the probability of differing expenditures resulting in a specific change in average NAEP scores. At the present, there are no major conclusions we can draw from our current data exploration and model, but there are plenty of future directions that could offer promising insight into this data that will assist future education policy making and funding and expenditure decisions.

\
