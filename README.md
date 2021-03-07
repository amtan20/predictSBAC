# predictSBAC
Final Project for MSDS699 Machine Learning Laboratory

# Introduction
The goal of this project was to develop a binary classification machine learning model that could predict whether or not a student will pass the Math SBAC (California's end of year exam). 

My interest in creating this model stems from my five years of experience as a middle school and high school math teacher. Teachers have access to hundreds of different datapoints about their students, but the challenge is knowing which datapoints are most indicative of a student's future success. We already know that performance on the MAP test is highly predictive of student SBAC performance: students in the top quartile usually pass and students in the bottom quartile usually don't pass. However, for students in the 2nd and 3rd quartiles, it becomes more challenging to predict whether or not they will pass.

Students who are in the bottom quartlie generally get the majority of the teacher's attention, but there are 2nd and 3rd quartile students in need of extra help that often get overlooked. This model attempts to address the issue of overlooking those borderline students.   

# Use Case For the Model

The model uses student demographic information and assessment data from the first semester. Teachers would run this model in January to get a better understanding of which students are predicted to pass and which students are predicted to fail, paying close attention to the predictions for the borderline students - the students who are in the 2nd and 3rd quartiles. The borderline students who are predicted to fail would then be given extra support: extra check-ins during class, pulling them into teacher-guided small groups during worktime, or inviting them to after school tutoring sessions, to name a few. With a little bit of extra support in the second semester, these borderline students would be put on track to pass the SBAC at the end of the year. 

# Data
The data is from students at a single middle school in the 2018-2019 school year. I received written permission from the school leader to use this student data for this project. All identifying information was removed in order to comply with FERPA student privacy guidelines. 

# Collab Link
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amtan20/predictSBAC/blob/main/Final_Modeling_Notebook.ipynb)

# Evaluation Metrics 
I focused on 2 metrics: 
- precision
- accuracy

My goal is to produce a model that reduces false positives. A false positive means the model predicts that a student will pass SBAC when in reality they fail. This is problematic because it means there are students who should have received extra support during the school year did not receive it because the model did not identify them as being on track to fail. For this reason, precision is the most important metric in this project. 

I was also interested in accuracy because I wanted to know how well the model does at classifying whether or not a student will pass or fail. I debated whether to use accuracy or balanced accuracy. Balanced accuracy is better when there are class imbalances, but since the target had about a 70/30 split between the two classes, I decided this was not enough of a class imbalance to merit using balanced accuracy. Furthermore, balanced accuracy is defined as the average of recall obtained on each class. Recall is not as important for this case, so I stuck with accuracy score as my second metric. 

# Algorithms 
I searched for algorithms in two ways using both randomized cross validation search and manual search across 9 classification algorithms to see which had the highest precision. The three candidate models selected from this process were:
- Extra Trees Classifier
- Logistic Regression
- SGDC Classifier 

# Best Model 
After doing randomized cross validation to search to find the best hyperparameters, I compared the performance of the three models. 

Model | Precision | Accuracy
--- | --- | ---
Logistic Regression | 0.900 | 0.822
SGD | 0.875 | 0.877
Extra Trees | 0.860 | 0.877

# Most Important Features  
The features that were most important for making predictions 

# Limitations of the Model & Future Directions 

