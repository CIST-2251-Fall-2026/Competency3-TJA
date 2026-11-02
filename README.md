# Competency3-TJA
## Project Overview
This project explores machine learning approaches for classifying dry bean varieties using numerical measurements obtained from bean images.

The goal is to compare multiple machine learning algorithms and determine which model would be the most appropriate for a production prototype for an agricultural sorting company.

The project also explores unsupervised learning to determine whether natural groupings exist within the bean measurements when variety labels are not provided.

The analysis includes both supervised classification and unsupervised clustering.
## Buisness Problem
An agricultural sorting company wants to automate the identification of dry bean varieties using measurements collected by a camera system.

The company wants a machine learning model that can consistently predict bean varieties while considering:

-Prediction accuracy.

-Processing and prediction speed.

-Model complexity.

-Maintainability.

-Explainability.

The goal is not simply to select the model with the highest accuracy but to recommend a model that balances predictive performance with practical business requirements.

## Dataset
The project uses the Dry Bean dataset from the UCI Machine Learning Repository.

The dataset contains:

13,611 bean samples.
16 numerical features.
7 bean varieties.

The features describe the shape and dimensions of individual beans.

The target variable is Class, which identifies the bean variety.

The dataset is used for supervised classification and unsupervised clustering.

For clustering, the target labels are excluded from the algorithm so that the model can identify groupings using measurements alone.

### Dataset Citation
Koklu, M., and Ozkan, I. A. (2020). Dry Bean [Dataset]. UCI Machine Learning Repository.

https://doi.org/10.24432/C50S4B

License: CC BY 4.0.

## Data Preparation
The dataset was downloaded using the UCI Machine Learning Repository Python package.

The numerical measurements were stored in X, while the bean variety classifications were stored in y.

The dataset was divided into training and testing sets using an 80/20 split.

Stratified sampling was used to preserve the distribution of bean varieties.

Feature scaling was applied where appropriate using StandardScaler.

Machine learning preprocessing was performed through pipelines where appropriate to prevent data leakage.

## Supervised Machine Learning Models
Four classification approaches were evaluated.

### Logistic Regression
Logistic Regression was used as the baseline model.

It provides a relatively simple approach to multiclass classification and establishes a performance benchmark for the more complex algorithms.

### Decision Tree
A Decision Tree was used to examine how a rule-based classification model performs.

Its structure also provides an opportunity to visualize and explain classification decisions.

### Random Forest
Random Forest combines multiple decision trees to improve predictive performance and reduce the instability of an individual decision tree.

Feature importance was examined to investigate which measurements contributed most to predictions.

### HistGradientBoosting
HistGradientBoosting was used as a boosting-based ensemble approach.

It builds models sequentially to improve upon earlier prediction errors.

## Model Evaluation
The models were compared using stratified five-fold cross-validation on the training dataset.

The final model evaluations were performed using the same held-out testing dataset.

Evaluation measurements included:

Training accuracy.

Testing accuracy.

Macro F1-score.

Cross-validation accuracy.

Cross-validation variability.

Training time.

Prediction time.

A confusion matrix and classification report were also generated to examine performance across the seven bean varieties.

## Overfitting and Underfitting
Training and testing performance were compared to investigate model generalization.

A substantial difference between training and testing performance may indicate overfitting.

Similarly, consistently low training and testing performance may indicate underfitting.

Cross-validation results were also examined to evaluate model stability.

The observations from these experiments are discussed in the Jupyter Notebook.

## Unsupervised Learning and Clustering
K-Means clustering was used to investigate natural groupings within the Dry Bean measurements.

The clustering algorithm received only the numerical measurements and did not receive the actual bean variety labels.

StandardScaler was applied before clustering because K-Means relies on distance calculations.

The Elbow Method and Silhouette Scores were used to investigate appropriate cluster counts.

Seven clusters were also examined to explore potential relationships with the seven known bean varieties.

After clustering, the discovered groups were compared with the actual labels using:

Cluster comparison tables.
Adjusted Rand Index.
Normalized Mutual Information.
PCA visualizations.
The actual variety labels were used only for post-clustering evaluation.

Cluster numbers were not assumed to correspond directly to bean varieties.

## Production Model Recommendation
The recommended model is:

__Logistic Regression__

It has average test accruacy but is much faster when sorting each bean so depending on the hardware can sort more bean per hour than any other model.

The recommendation is based on the experimental results and the customer's business requirements.

The decision considers prediction quality, speed, maintainability, complexity, and explainability.

The selected model represents a candidate for a production prototype rather than a fully validated production system.

Additional testing with actual camera hardware and real-world sorting conditions would be required before deployment.

## AI Use

AI was used to create the outline for the readme.md and quickly convert some results to useful visual graphs using both seaborn and matplot.lib.

