# E-Commerce Revenue Prediction

## Dataset (provided):

- This dataset contains transactions occurring in an online store (E-commerce).
- Out of the 12,330 customer samples in the dataset, 84.5% (10,422) were negative class samples (i.e. customers who did not end up buying the product), and the rest (1908) were positive class samples (i.e. customers who ended up buying).
- The dataset consists of 6 numerical and 12 categorical attributes while the 'Revenue' attribute can be used as the class label.
- "Administrative", "Administrative Duration", "Informational", "Informational Duration", "Product Related" and "Product Related Duration": These represent the number of different types of pages visited by the visitor in that session and total time spent in each of these page categories. The values of these features are derived from the URL information of the pages visited by the user and updated in real time when a user takes an action, e.g. moving from one page to another.
- The "Bounce Rate", "Exit Rate" and "Page Value" features represent the metrics measured by "Google Analytics" for each page in the e-commerce site:

  - Bounce Rate: The value of "Bounce Rate" feature for a web page refers to the percentage of visitors who enter the site from that page and then leave ("bounce") without triggering any other requests to the analytics server during that session.
  - Exit Rate: The value of "Exit Rate" feature for a specific web page is calculated as for all pageviews to the page, the percentage that were the last in the session.
  - Page Value: The "Page Value" feature represents the average value for a web page that a user visited before completing an e-commerce transaction.

- The "Special Day" feature indicates the closeness of the site visiting time to a specific special day (e.g. Mother’s Day, Valentine's Day) in which the sessions are more likely to be finalized with transaction. The value of this attribute is determined by considering the dynamics of e-commerce such as the duration between the order date and delivery date. For example, for Valentina’s day, this value takes a nonzero value between February 2 and February 12, zero before and after this date unless it is close to another special day, and its maximum value of 1 on February 8.
- The dataset also includes operating system, browser, region, traffic type, visitor type as returning or new visitor, a Boolean value indicating whether the date of the visit is weekend, and month of the year.

## Description:

For this problem, 7 models will be run for each of the three metrics (ROC AUC, Accuracy, F1-score):

- Logistic Regression
- K Nearest Neighbor
- Random Forest
- Light Gradient Boosting Machine
- XGBoost
- Voting Classifier using the first 5 models
- Stacking Classifier using first 4 models as estimators and final estimator is XGBoost.

## Installation:

We will use `python=3.8.10` and in order to install the independencies: `pip install -r requirements.txt`.

To deploy a certain model, we will be using `joblib` (a better version of pickle). The format is `model_clf_metric.joblib`. For example, if we want to deploy a random forest model which is tuned for F1-score then the model file is `rf_clf_f1.joblib` and we run:

```
import joblib

clf = joblib.load('/path/to/file/rf_clf_f1.joblib')
predictions = clf.predict(X_test)
```
