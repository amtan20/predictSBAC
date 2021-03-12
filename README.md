# predictSBAC
Final Project for MSDS699 Machine Learning Laboratory

# Introduction
The goal of this project was to develop a binary classification machine learning model that could predict whether or not a student will pass the Math SBAC (California's end of year exam). 

My interest in creating this model stems from my five years of experience as a middle school and high school math teacher. As a teacher, I had access to hundreds of different datapoints about my students, but the challenge was to know which datapoints could predict a student's future success. I already knew that performance on the MAP test is highly predictive of student SBAC performance: students in the top quartile usually pass and students in the bottom quartile usually don't pass. However, for students in the 2nd and 3rd quartiles, it was more challenging to predict whether or not they will pass. I was tired of seeing students who seemed to be doing well in class end up failing the SBAC. I wanted to build a model to help teachers identify more of these borderline students. 

# Use Case For the Model

The model uses student demographic information and assessment data from the first semester. Teachers would run this model in January to get a better understanding of which students are predicted to pass and which students are predicted to fail, paying close attention to the 2nd and 3rd quartile students. These borderline students who are predicted to fail would then be given extra support: extra check-ins during class, pulling them into teacher-guided small groups during worktime, or inviting them to after school tutoring sessions, to name a few. With a little bit of extra support in the second semester, these borderline students would be put back on track to pass the SBAC at the end of the year. 

# Data
The data is from students at a single middle school in the 2018-2019 school year. I received written permission from the school leader to use this student data for this project. All identifying information was removed in order to comply with FERPA student privacy guidelines. 

# Collab Link
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amtan20/predictSBAC/blob/main/Final_Notebook.ipynb)


# Evaluation Metrics 
I focused on 2 metrics: precision and accuracy

**Precision:** 
- Since the goal is to produce a model that reduces false positives, precision is the best way to measure the model's performance.
- A false positive means the model predicts that a student will pass SBAC when in reality they fail. This is problematic because it means there are students who should have received extra support during the school year did not receive it because the model did not identify them as being on track to fail.

**Accuracy:** 
- It is also important to know the overall accuracy of the model. Given that the target class had a 66/34 split, it is important to make sure the model outperforms the a priori probability (meaning the model needs to achieve an accuracy score of 0.66 or higher)
- I debated whether to use accuracy or balanced accuracy. Balanced accuracy is better when there are class imbalances, but since the target had about a 66/34 split between the two classes, I decided this was not enough of a class imbalance to merit using balanced accuracy. Furthermore, balanced accuracy is defined as the average of recall obtained on each class. Recall is not as important for this case, so I stuck with accuracy score as my second metric.


# Algorithms 
I did a randomized cross validation search across 9 classification algorithms to see which had the highest precision. The three candidate models selected from this process were:
- Extra Trees Classifier
- Logistic Regression
- SGDC Classifier 

# Best Model 
After doing randomized cross validation to search to find the best hyperparameters, I compared the cross validated scores of the three models. 

Model | Precision | Accuracy
--- | --- | ---
Logistic Regression | 0.909 | 0.837
SGD | 0.851 | 0.830
Extra Trees | 0.856 | 0.851

Since Logistic Regression had the highest precision and second highest accuracy, I selected it as my final model. 

# Most Important Features  
The fewer the features in a logistic regression model, the more general the model becomes. I used permutation importance to see which features were most important to the model and kept only the top 5 most important features. My model went from having 23 features to 5 features and the model's precision increased by 0.03 after simplifying the model. 

# Performance on the Test Set 
 Metric | Precision | Accuracy
--- | --- | ---
Train | 0.939 | 0.872
**Test** | **0.922** | **0.876**


# Conclusions 
**The model performed similarly on the test set as the train set**
<br>The final model has good generality. 

**The model minimizes false positives**
<br>The final model does a good job of correctly predicting students who will pass the SBAC. The model was selected and tuned to minimize the chance of false positives. In the test set, only 5 students are predicted to pass when in reality they failed. This model can help teachers identify students that need extra support who would have otherwise gone unnoticed.

**The model's accuracy beats the a priori probability**
<br> The model's accuracy of 0.88 is well above the a priori probability of 0.66, but there is still room for improvement.

**Areas for improvement**
<br> There is a big gap in the model's precision for class 0 (fail) and class 1 (pass). I would like to improve the model's ability to minimize false negatives, thereby improving overall accuracy.

# Future Directions 
- Retrain the model using only data from Q2 and Q3 students
- Obtain data from multiple years. Data in this project was from a single school year. 
- Re-do as a multi-class classification problem, with special attention to predicting the Standard Nearly Met class 

