# Personal Loan Acceptance Prediction

Machine learning classification model using k-Nearest Neighbors (k=13), achieving 91.05% accuracy in predicting customer loan acceptance behavior.

Banks spend heavily on loan marketing campaigns that target the wrong customers. This project builds a classifier that flags which customers are actually likely to accept a personal loan offer, so campaigns can be targeted instead of broad.

## Project Overview

Built a predictive model to help banks:
- Identify likely loan acceptors
- Reduce marketing costs
- Improve campaign targeting
- Optimize sales strategies

## Methodology

I started with a single nearest neighbor (k=1) baseline model to establish a floor for performance, then moved to grid search optimization, testing k values of 1, 13, and 25 using 10-fold nested cross-validation. k=13 gave the best cross-validated accuracy, striking a balance between overfitting (k=1) and over-smoothing with a larger k. ![k-Nearest Neighbors Model Output](01-knn-classification.png)

Cross-validation results at k=13:
- CV Accuracy: 90.23% ± 0.80%
- Precision (acceptor): 46.75%
- Recall (acceptor): 12.50%
- Class Precision (non-acceptor): 91.38%

I then evaluated the model on a 40% holdout set it hadn't seen during training.

| Metric | Value |
|---|---|
| Accuracy | 91.05% |
| Precision (acceptor) | 63.83% |
| Recall (acceptor) | 15.62% |
| Specificity (non-acceptor) | 99.06% |

The model holds up well on unseen data, staying around 91% accuracy. It's excellent at correctly ruling out people who won't accept a loan, but it only catches a small share of the people who would. That's a direct result of class imbalance in the training data. Far more people decline than accept, so the model naturally leans toward predicting no.

## Key Findings

- Model achieves 91% accuracy on unseen data
- Excellent at identifying non-acceptors, with 99.06% specificity
- Class imbalance limits recall for actual acceptors
- Strong baseline for loan targeting strategies, though not yet optimized for catching every likely acceptor

## What I Would Do Differently

Given more time, I would apply SMOTE or another resampling approach to address the class imbalance directly, rather than relying on grid search alone. Recall on the acceptor class is the real weak point here, and it's the metric that matters most to a bank trying not to miss real prospects.

## Tools and Technologies

RapidMiner Studio, k-Nearest Neighbors, Grid Search, 10-Fold Cross-Validation, Confusion Matrix Analysis

## Business Recommendations

1. Deploy the model as an initial screening layer, not a final decision
2. Address class imbalance with SMOTE or threshold tuning to improve recall
3. Pair with rule-based filters to catch acceptors the model misses
4. Retrain quarterly as new customer data comes in

## Author

Pratima Kandel
MS in Business Analytics, Webster University
St. Louis, MO
Open to Business Analyst & Data Analyst roles

If you found this project helpful, feel free to star the repo.
