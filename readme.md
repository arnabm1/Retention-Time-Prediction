# Retention-Time-Prediction

This repository contains notebooks for predicting the retention time of a given molecule in a liquid chromatography experiment. The two folders include the notebooks for each experiment along with the predicted CSV.

# Required Packages
1) Python
2) Pandas
3) Numpy
4) Scikit-learn
5) rdkit

# Intuition and Solution

The problem statement specifies that the retention time depends on two factors: (1) the chemical structure of the molecule and (2) the chromatography platform used in a particular laboratory. Therefore, the expectation is that if the retention time is experimentally measured for a certain number of molecules on a particular laboratory’s chromatography, it should be possible to predict the retention times of other unmeasured molecules. The task of prediction, in this case, is based on correlating features (molecule structure and lab) to outcomes or numerical outcomes (retention time). The training set includes molecular structure, lab name, and corresponding retention time in a CSV file. The CSV file is parsed to separate the retention time and use it as training outputs. 

To this extent, I explore two machine learning models, i.e., 

**1) Random Forest and**

**2) Gradient Boosting** (As per the suggested experiments in the [paper](https://analyticalsciencejournals.onlinelibrary.wiley.com/doi/full/10.1002/jssc.202000060)). 

Due to the limited number of features, the problem can be solved using tree-based structures (e.g., decision trees) and regression frameworks. I particularly used random forest and gradient boost methods because they have a rather quick execution time compared to decision trees.

To generate the features from the molecular structures I used the rdkit library widely used for chemical informatics. The **SMILE molecular notations are first converted to structures** using the rdkit library. Then I created **ECFP (i.e., connectivity fingerprints) representations of the same structures so that it is possible to convert them to numerical values. The numerical values thus gained are concatenated with the one-hot encoded lab information to create the training and testing data.** The models are trained on these to create the predictions. Predicted retention times are saved into a CSV file after the models are trained.
