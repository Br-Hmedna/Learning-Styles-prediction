# A Predictive Model for the Identification of Learning Styles in MOOC Environments
The objective of this study is to predict learners’ learning styles based on their learning traces. 
# Dataset
The data used in this study were collected from an edX course entitled “Statistical Learning” conducted in Winter
2015 and Winter 2016 by the University of Stanford.The data were generously offered by the Center for Advanced
Research through Online Learning (CAROL). Data were anonymized to protect the privacy of students.
The course lasted nine weeks and consisted of lecture videos, problems and a discussion forum. Table
1 shows the most relevant information about this dataset, indicating the number of enrolled learners and
events left by learners.

# Methodology
the overall architecture of our proposed method, consists of five main phases:
![](methodology.png)

## Data collection:
The database of the current study were collected from an edX course entitled “Statistical Learning (Session Winter 2015 and Winter 2016)”, administered via Stanford’s Logunita platform. The sequential activities performed by each learner during each session were collected.
## Data preprocessing:
This step was carried out in order to improve the quality of the data to be analyzed. An anomaly detection process was applied in order to
obtain valid data by excluding contaminated traces. A feature extraction step was then conducted to convert
the learner’s traces into a list of features for the machine learning algorithms to process. Following this, a normalization process was applied to scale the data for
machine learning algorithms such K-means and nearest neighbor; these approaches are sensitive to data scaling, and normalization means that they can be used without deterioration in performance. Finally, feature selection was performed in order to select the most significant features related to each pole (learning style) of
the three selected dimensions of FSLSM (processing, input and understanding).
## Unsupervised modeling: 
The resulting features associated with each pole were used as input to cluster learners into groups according to their degree of preference for each pole. Each cluster is labeled with a class (very_weak, weak, moderate, strong) that best describes the level of preference for each pole. The clustering results were stored in a separate csv file (csv_active, csv_reflective, csv_visual, csv_verbal, csv_global, and csv_sequential), each of which contained the features and the class representing the level of preference of the 
learning style
## Aggregation: 
We merged each pair of files related to a given dimension, and then generated three csv files (csv_processing, csv_input, csv_understanding).
## Supervised modeling: 
The resulting data from the aggregation process was split randomly into training and test sets. The training set was used in training
the classifiers, while the test set was used to evaluate the performance of the trained algorithms. This standard process of dividing a dataset ensures that all feature vectors for a given learner reside in a single dataset, thus eliminating the possibility of training and testing the model on data from the same learner. To ensure
generalizability, we trained four popular machine learning algorithms: the decision tree, random forest, Knearest neighbor and a neural network. These were applied to a large training set and their hyper-parameters tuned automatically using a grid search with 10-fold cross-validation before testing the models on the test
set (10,514 learners). Finally, the optimal model based on these results was chosen as the predictive model of learning styles.
