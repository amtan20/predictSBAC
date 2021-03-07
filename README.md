# predictSBAC
Final Project for MSDS699 Machine Learning Laboratory

# Introduction
The goal of this project was to develop a binary classification machine learning model that could predict whether or not a student will pass the Math SBAC (California's end of year exam). 

My interest in creating this model stems from my five years of experience as a middle school and high school math teacher. Teachers have access to hundreds of different datapoints about their students, but the challenge is knowing which datapoints are most indicative of a student's future success. We already know that performance on the MAP test is highly predictive of student SBAC performance: students in the top quartile usually pass and students in the bottom quartile usually don't pass. However, for students in the 2nd and 3rd quartiles, it becomes more challenging to predict whether or not they will pass.

Students who are in the bottom quartlie generally get the majority of the teacher's attention, but there are 2nd and 3rd quartile students in need of extra help that often get overlooked. This model attempts to address the issue of overlooking those borderline students.  This model can be used by teachers during the school year to help make better-informed decisions about which students to target for extra support with the goal of increasing the number of students who pass the SBAC. 

# Use Case For the Model

The model uses student demographic information and assessment data from the first semester. Teachers would run this model in January to get a better understanding of which students are predicted to pass and which students are predicted to fail, paying close attention to the predictions for the borderline students - the students who are in the 2nd and 3rd quartiles. The borderline students who are predicted to fail would then be given extra support: extra check-ins during class, pulling them into teacher-guided small groups during worktime, or inviting them to after school tutoring sessions, to name a few. 

The theory is that with a little bit of extra support in the second semester, these borderline students would be put on track to pass the SBAC at the end of the year. 

# Data
The data is from students at a single middle school in the 2018-2019 school year. I received written permission from the school leader to use this student data for this project. All identifying information was removed in order to comply with FERPA student privacy guidelines. 

# Algorithms 
I searched for algorithms in two ways. First, I did a randomized cross validation search across 9 classification algorithms to see which had the highest precision - it found Extra Trees Classifier to be the best. It only returns one best model, so I did a second search with the same 9 algorithms to find two other candidate models. To do this, I looped through the algorithms, fit each algorithm 100 times, and calculated the average precision and accuracy scores. Logistic Regression and Extra Trees Classifier were in the top 3 for both precision and accuracy. It was reassuring that Extra Trees Classifier came up as a top model in both search processes. Since I care more about precision, I selected SGDC Classifier as my third candidate algorithm, since it was the top performing algorithm for precision. 

3 candidate models:
- Extra Trees Classifier
- Logistic Regression
- SGDC Classifier 

# Evaluation Metrics 
I focused on 2 metrics: precision and accuracy. 

My goal is to produce a model that reduces false positives. A false positive means the model predicts that a student will pass SBAC when in reality they fail. This is problematic and needs to be avoided because it means there are students who should have received extra support during the school year did not receive it because the model did not identify them as being on track to fail. 

I was also interested in accuracy because I wanted to know how well the model does at classifying whether or not a student will pass or fail. I debated whether to use accuracy or balanced accuracy. Balanced accuracy is better when there are class imbalances, but since the target had about a 70/30 split between the two classes, I decided this was not enough of a class imbalance to merit using balanced accuracy. Furthermore, balanced accuracy is defined as the average of recall obtained on each class. Recall is not as important for this case, so I stuck with accuracy score as my second metric. 

# Findings 
The features that were most important for making predictions 

# Limitations of the Model & Future Directions 

