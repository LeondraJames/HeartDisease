# Heart Disease Prediction (Logistic Regression)
"What Your Heart Is Telling You" Logit Model (DataCamp Project)
The following is a notebook project / assignment in Datacamp which can be found here: https://www.datacamp.com/projects/445

The following steps were taken to predict heart disease classification. 

1. Heart disease and potential risk factors
Millions of people are getting some sort of heart disease every year and heart disease is the biggest killer of both men and women in the United States and around the world. Statistical analysis has identified many risk factors associated with heart disease such as age, blood pressure, total cholesterol, diabetes, hypertension, family history of heart disease, obesity, lack of physical exercise, etc. In this notebook, we're going to run statistical testings and regression models using the Cleveland heart disease dataset to assess one particular factor -- maximum heart rate one can achieve during exercise and how it is associated with a higher likelihood of getting heart disease.

2. Converting diagnosis class into outcome variable
We noticed that the outcome variable class has more than two levels. According to the codebook, any non-zero values can be coded as an "event." Let's create a new variable called hd to represent a binary 1/0 outcome.

There are a few other categorical/discrete variables in the dataset. Let's also convert sex into 'factor' type for next step analysis. Otherwise, R will treat them as continuous by default.

3. Identifying important clinical variables
Now, let's use statistical tests to see which ones are related to heart disease. We can explore the associations for each variable in the dataset. Depending on the type of the data (i.e., continuous or categorical), we use t-test or chi-squared test to calculate the p-values.

4. Explore the associations graphically (i)
A good picture is worth a thousand words. In addition to p-values from statistical tests, we can plot the age, sex, and maximum heart rate distributions with respect to our outcome variable. This will give us a sense of both the direction and magnitude of the relationship.

5. Explore the associations graphically (ii)
Next, let's plot sex using a barplot since it is a binary variable in this dataset.

6. Explore the associations graphically (iii)
And finally, let's plot thalach using a boxplot since it is a continuous variable.

7. Putting all three variables in one model
The plots and the statistical tests both confirmed that all the three variables are highly significantly associated with our outcome (p<0.001 for all tests).

In general, we want to use multiple logistic regression when we have one binary and two or more predicting variables. The binary variable is the dependent (Y) variable; we are studying the effect that the independent (X) variables have on the probability of obtaining a particular value of the dependent variable. For example, we might want to know the effect that maximum heart rate, age, and sex have on the probability that a person will have a heart disease in the next year. The model will also tell us what the remaining effect of maximum heart rate is after we control or adjust for the effects from the other two effectors.

8. Extracting useful information from the model output
It's common practice in medical research to report Odds Ratio (OR) to quantify how strongly the presence or absence of property A is associated with the presence or absence of the outcome. When the OR is greater than 1, we say A is positively associated with outcome B (increases the Odds of having B). Otherwise, we say A is negatively associated with B (decreases the Odds of having B).

9. Predicted probabilities from our model
So far, we have built a logistic regression model and examined the model coefficients/ORs. We may wonder how can we use this model we developed to predict a person's likelihood of having heart disease given his/her age, sex, and maximum heart rate. Furthermore, we'd like to translate the predicted probability into a decision rule for clinical use by defining a cutoff value on the probability scale. In practice, when an individual comes in for a health check-up, the doctor would like to know the predicted probability of heart disease, for specific values of the predictors: a 45-year-old female with a max heart rate of 150. To do that, we create a data frame called newdata, in which we include the desired values for our prediction.

10. Model performance metrics
Are the predictions accurate? How well does the model fit our data? We are going to use some common metrics to evaluate the model performance. The most straightforward one is Accuracy, which is the proportion of the total number of predictions that were correct. On the opposite, we can calculate the classification error rate using 1- accuracy. However, accuracy can be misleading when the response is rare (i.e., imbalanced response). Another popular metric, Area Under the ROC curve (AUC), has the advantage that it's independent of the change in the proportion of responders. AUC ranges from 0 to 1. The closer it gets to 1 the better the model performance. Lastly, a confusion matrix is an N X N matrix, where N is the level of outcome. For the problem at hand, we have N=2, and hence we get a 2 X 2 matrix. It cross-tabulates the predicted outcome levels against the true outcome levels.

After these metrics are calculated, we'll see (from the logistic regression OR table) that older age, being male and having a lower max heart rate are all risk factors for heart disease. We can also apply our model to predict the probability of having heart disease. For a 45 years old female who has a max heart rate of 150, our model generated a heart disease probability of 0.177 indicating low risk of heart disease. Although our model has an overall accuracy of 0.71, there are cases that were misclassified as shown in the confusion matrix. Beyond this project, optimization measures should be considered to improve our current model by including other relevant predictors from the dataset into our model.
