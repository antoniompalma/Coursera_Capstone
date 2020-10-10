1.	Introduction
1.1 Background
This data is regarding Seattle, Washington state. Total number of personal vehicles in Seattle in the year 2016 was 444,000 vehicles. The increase in car ownership rates can lead to higher numbers of accidents on the road because of a simple probability.
1.2 Problem
The National Highway Traffic Safety Administration of the USA suggests that the economical and social harm from car accidents can cost more than $800 billion per year. According to 2017 WSDOT data, a car accident occurs every 4 minutes and a person dies due to a car crash every 20 hours in the state of Washington while Fatal crashes went from 508 in 2016 to 525 in 2017, resulting in the death of 555 people. This project´s goal is to predict severity of an accident and how it can be reduced based on some factors.
1.3 Stakeholders
The reduction in severity of accidents can be beneficial to Seattle Authority which works towards improving those road factors and the car drivers who may take precaution to reduce the severity of accidents.
2.	Understanding Data
2.1 Data Cleaning
The dataset has total observations of 194673 with variation in number of observations for every feature. First of all, the total dataset had high variation in the lengths of almost every column of the dataset. The dataset had a lot of empty columns which could have been beneficial had the data been present there. These columns included pedestrian granted way or not, segment lane key, crosswalk key and hit parked car. The models aim was to predict the severity of an accident, considering that, the variable of Severity Code was in the form of 1 (Property Damage Only) and 2 (Injury Collision) which were kept this way. Furthermore, the “Y” was given value of 1 whereas “N” and “no” value was given 0 for the variables Inattention, Speeding and Under the influence. For lighting conditions, Light was given 0 along with Medium as 1 and Dark as 2. For Road Condition, Dry was assigned 0, Mushy was assigned 1 and Wet was given 2. As for Weather Condition, 0 is Clear, Overcast is 1, Windy is 2 and Rain and Snow was given 3. 0 was assigned to the element of each variable which can be the least probable cause of severe accident whereas a high number represented adverse condition which can lead to a higher accident severity. Whereas, there were unique values for every variable which were either ‘Other’ or ‘Unknown’, deleting those rows entirely would have led to a lot of loss of data which is not preferred.
In order to deal with the issue of columns having a variation in frequency, arrays were made for each column which were encoded according to the original column and had equal proportion of elements as the original column. Then the arrays were imposed on the original columns in the positions which had ‘Other’ and ‘Unknown’ in them. This entire process of cleaning data led to a loss of almost 5000 rows which had redundant data, whereas other rows with unknown values were filled earlier.
2.2 Feature Selection
A total of 6 variables were selected for this project along with the target variable being Severity Code.
•	Underinfl - wether or not the driver was under the influence (Y/N)
•	Weather - Weather condition during time of collision (ovecast/rain/clear)
•	Roadcond - road condition during collision (wet/dry)
•	Lightcond - light condition during collision (lights on/dark with lights on) 
•	Speeding – whether driver was above speed limit or not
•	InnattentionInd – whether or not collision was due to inattention 

3.	Methodology
The variables above were selected because they are commonly known as the top causes for car accidents.  
After looking at data and making some cleaning, was noted that dataset is supervised but unbalanced and target variable was close to 2:1 ratio in favor of property damage. Because of this, and to try to have balanced data so machine learning algorithms are feasible  I have used the function smote from imblearn library in order to balance the target variable in equal proportions and to have neutral classification model which is trained on equal instances of both the elements under severity of accidents.
The factor with most number of accidents under adverse conditions was adverse weather while adverse lighting condition was second. The factors that have less contribution were over-speeding and under the influence.
Machine Learning Models used were:
k-Nearest Neighbor: is an algorithm for supervised learning. Where the data is 'trained' with data points corresponding to their classification. Once a point is to be predicted, it takes into account the 'K' nearest points to it to determine it's classification. 
Decision Tree Analysis: The Decision Tree Analysis breaks down a data set into smaller subsets while at the same time an associated decision tree is incrementally developed. The final result is a tree with decision nodes and leaf nodes.
Logistic Regression: Logistic Regression is a variation of Linear Regression, useful when the observed dependent variable, y, is categorical. It produces a formula that predicts the probability of the class label as a function of the independent variables.
4.	Results
The results of the three models had variations between them, one worked very well at predicting the positives accurately while the other predicted the negatives better.
Decision Tree The criterion chosen for the classifier was entropy and the max depth was 6.
Logistic Regression The C used for regularization strength was 0.01 whereas the solver used was liblinear.
k-Nearest Neighbor The best K, as shown below, for the model is at 4.
5.	Model Accuracy
Precision: Precision refers to the percentage of results which are relevant, in simpler terms it can be seen as how many of the selected items from the model are relevant. Mathematically, it is calculated by dividing true positives by true positive and false positive Recall: Recall refers to the percentage of total relevant results correctly classified by the algorithm. In simpler terms, it tells how many relevant items were selected. It is calculated by dividing true positives by true positive and false negative F1-Score: f1-score is a measure of accuracy of the model, which is the harmonic mean of the model’s precision and recall. Perfect precision and recall is shown by the f1-score as 1, which is the highest value for the f1-score, whereas the lowest possible value is 0 which means that either precision or recall is 0
6.	Conclusion
When comparing all the models by their f1-scores, Precision and Recall, we have a clearer picture in terms of the accuracy of the three models individually as a whole and how they perform for each output of the target variable. When comparing these scores, we can see that the f1-score is highest for k-Nearest Neighbor at 0.75. However, later when we compare the precision and recall for each of the model, we can see that the k-Nearest Neighbor model performs poorly in the precision of 1 at 0.08. The variance is too high for the model to be selected as a viable option. When looking at the other two models, we can see that the Decision Tree has a more balanced precision for 0 and 1. Whereas, the Logistic Regression is more balanced when it comes to recall of 0 and 1. Furthermore, the average f1-score of the two models are very close but for the Logistic Regression it is higher by 0.04. It can be concluded that the both the models can be used side by side for the best performance.
7.	Recommendations
After evaluating the data and the output of the Machine Learning models, a few recommendations can be made. 
Looking that almost all the accidents have occurred on a block or an intersection, more traffic lights, safety signs or better light conditions could be implemented to improve road conditions and reduce number of accidents.
Also, regarding the concentration of accidents, it can be seen that most of them are on the main roads, near the highway in the city center. The car drivers could also use this data to assess when to take extra precautions on the road under the given circumstances of light condition, road condition and weather, especially near or around I-5.
