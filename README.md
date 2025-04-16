# Adaboost-classifier
The objective of this project is to create a binary AdaBoost classifier that utilizes weighted weak linear classifiers as its base learners. In contrast to typical decision stumps, weighted weak linear classifiers can take into account the overall structure of the data, leading to more adaptable and efficient decision boundaries. This project emphasizes the complete implementation of the AdaBoost algorithm from the ground up, developing the weak learners, and incorporating them into a strong ensemble model. This implementation allows for an examination of both the theoretical and practical components of ensemble learning, a key domain in machine learning. Methods like AdaBoost are popular 
because they can boost the performance of weak classifiers, improve generalization, and effectively manage difficult datasets with intricate decision boundaries. These advantages establish AdaBoost as a fundamental algorithm in supervised learning applications. 
In addition to building the classifier, this project also involves: 
  ●  Visualizing Decision Boundaries  : To observe how the ensemble model evolves and adapts to the data over iterations. 
  ●  Performance Evaluation  : To measure the effectiveness of the model in terms of accuracy on training and testing datasets. 
  ●  Analysis of Weak Learners  : To determine key metrics, including: 
        ○  The number of weak learners (n) needed to achieve 100% accuracy on the training set. 
        ○  The maximum achievable accuracy on the testing set and the number of weak learners (n  test) required to achieve it. 
        ○  Whether the model can achieve 100% accuracy on the testing set.

The project involves: 
  ●  Implementing a weighted weak linear classifier. 
  ●  Designing an AdaBoost algorithm that uses these classifiers as base learners. 
  ●  Evaluating the model's performance on a training and testing dataset. 
  ●  Determining: 
        1.  The number of learners needed for attaining 100% training accuracy. 
        2.  The maximum achievable testing accuracy. 
        3.  Whether 100% testing accuracy is achievable or not. 
        4.  The number of learners that yield the best testing accuracy. 

Datasets: 
●  Training Dataset  : adaboost-train-24.txt 
●  Testing Dataset  : adaboost-test-24.txt


OVERVIEW OF ADABOOST AND WEIGHTED WEAK LINEAR CLASSIFIER 

ADABOOST 
AdaBoost, short for  Adaptive Boosting  , is an ensemble learning technique that combines multiple weak classifiers into a single strong classifier. Unlike traditional machine learning algorithms, which train a single model to predict outcomes, AdaBoost iteratively trains a series of weak classifiers, each focusing on the mistakes of its predecessors. By doing so, it improves the model's ability to generalize and handle challenging datasets. The implementation is inspired by the ideas sketched out in Flach's "Machine Learning" and adapted to work with AdaBoost-style "weight-distributions". 
The steps to build this model are as follows: 
1.  Initialise the Weights 
2.  Train Weak Classifier 
3.  Calculate Weighted Error 
4.  Update Weak Learner Weight (alpha) 
5.  Update Sample Weights 
6.  Normalise the Sample Weight 
7.  Combine Weak Classifiers
   
WEIGHTED WEAK LINEAR CLASSIFIER 
The weighted weak linear classifier is designed to use the weighted means of the classes to determine the decision boundary. Unlike Flach's approach, the classification boundary is not placed midway between the class means. Instead, the classifier uses the weighted means to calculate the orientation vector and find the best split based on weighted projections. 


IMPLEMENTATION 
1. WEAK LEARNER DESIGN 
The weighted weak linear classifier(  class CustomWeightedWeakLinearClassifier  ) serves as the base learner for AdaBoost. It was implemented to handle: 
  ●  Class Mean Calculation: 
      ○  Weighted means of the features were calculated for each class (+1 and −1), weighted by sample importance (distribution of weights). 
  ●  Orientation Vector: 
      ○  The orientation vector was defined as the difference between the weighted means of the two classes, normalized to ensure directionality. 
  ●  Threshold and Polarity: 
      ○  Data points were projected onto the orientation vector, and possible split points were evaluated to minimize classification error. 
      ○  The threshold was determined as the midpoint between consecutive projections, and the optimal polarity was selected based on the minimum error.
   
2. ADABOOST ALGORITHM 
The AdaBoost implementation trains weak classifiers iteratively, adjusting sample weights to focus on misclassified points: 
  1.  Initialize weights uniformly 
  2.  For each weak learner  : 
      ○  Train the classifier using current weights. 
      ○  Compute its weighted error 
      ○  Calculate the Weak Learner Weight (alpha) 
      ○  Update weights 
      ○  Normalize weights to ensure ∑wi= 1. 
  3.  Combine weak classifiers into a strong classifier

3. EVALUATION OF ADABOOST CLASSIFIER 
We have evaluated the performance of the AdaBoost classifier and visualized its behavior. The evaluation process involves fitting the AdaBoost model to the training data, predicting on both the training and testing datasets, and collecting accuracy trends as the number of weak learners increases. The  evaluate_custom_adaboost  function is used to evaluate the performance of the AdaBoost model. It takes in the training data, training labels, testing data, testing labels, and the number of learners as inputs. 
The function performs the following steps: 
    1.  Model Initialization  : The AdaBoost model is initialized with the specified number of learners. 
    2.  Model Training  : The model is fitted on the training data. 
    3.  Predictions  : The model makes predictions on both the training and testing datasets. 
    4.  Accuracy Calculation  : The training and testing accuracies are calculated by comparing the predictions with the actual labels. 
    5.  Return Values  : The function returns the training and testing accuracies.
  
The evaluation process involves fitting the AdaBoost model to the training data and predicting on both the training and testing datasets. The accuracy trends are collected as the number of weak learners increases.
1.  Initialization 
    ●  The maximum number of learners (num_learners) is set to 200. 
    ●  Lists training_accuracies and testing_accuracies are initialized. These are used to store accuracy values. 
    ●  Variables num_train_learners and num_test_learners are initialized.These are used to track the number of learners required to achieve 100% training accuracy and the maximum testing accuracy, respectively. 
2. Training and Prediction 
For each number of learners from 1 to num_learners: 
    ●  The AdaBoost model is initialized and fitted to the training data. 
    ●  Predictions are made on both the training and testing datasets. 
    ●  The accuracies are calculated and appended to the respective lists. 
    ●  The number of learners required to achieve 100% training accuracy and the maximum testing accuracy are tracked. 
3. Results 
    ●  The results are printed, showing the number of learners required to achieve 100% training accuracy and the maximum testing accuracy. 
    ●  The accuracy trends are printed in a tabular format.
