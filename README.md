# Adaboost-classifier
The objective of this project is to create a binary AdaBoost classifier that utilizes weighted weak linear classifiers as its base learners. In contrast to typical decision stumps, weighted weak linear classifiers can take into account the overall structure of the data, leading to more adaptable and efficient decision boundaries. This project emphasizes the complete implementation of the AdaBoost algorithm from the ground up, developing the weak learners, and incorporating them into a strong ensemble model. This implementation allows for an examination of both the theoretical and practical components of ensemble learning, a key domain in machine learning. Methods like AdaBoost are popular 
because they can boost the performance of weak classifiers, improve generalization, and effectively manage difficult datasets with intricate decision boundaries. These advantages establish AdaBoost as a fundamental algorithm in supervised learning applications. 
In addition to building the classifier, this project also involves: 
1. Visualizing Decision Boundaries  : To observe how the ensemble model evolves and adapts to the data over iterations.
2. Performance Evaluation  : To measure the effectiveness of the model in terms of accuracy on training and testing datasets.
3. Analysis of Weak Learners  : To determine key metrics, including:
   1. The number of weak learners (n) needed to achieve 100% accuracy on the training set.
   2. The maximum achievable accuracy on the testing set and the number of weak learners (n  test) required to achieve it.
   3. Whether the model can achieve 100% accuracy on the testing set.

The project involves: 
1. Implementing a weighted weak linear classifier.
2. Designing an AdaBoost algorithm that uses these classifiers as base learners.
3. Evaluating the model's performance on a training and testing dataset.
4. Determining: 
   1. The number of learners needed for attaining 100% training accuracy. 
   2. The maximum achievable testing accuracy. 
   3. Whether 100% testing accuracy is achievable or not. 
   4. The number of learners that yield the best testing accuracy. 

Datasets: 
1. Training Dataset  : adaboost-train-24.txt
2. Testing Dataset  : adaboost-test-24.txt
