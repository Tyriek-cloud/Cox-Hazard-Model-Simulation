# Cox-Hazard-Model-Simulation
<img width="1127" alt="image" src="https://github.com/user-attachments/assets/016ca25b-1ce4-4b06-ae43-b145a72823f5" />
The purpose of this project was to compare the base performance of three different Cox Proportional-Hazards Models on a set of synthetic/fake data. This synthetic data science project was designed to mimic a task that I was assigned at my work. I was tasked with looking at customer churn/retention for a subscription service (via our Saas app). The data that I worked with in all three models (and in my day job) included the following:

1. IVs: Age, biological sex, income, usage frequency, engagement, satisfaction ratings.
2. DVs: Changes in use of the subscription.
3. Confounding: Time of the year and service changes (outages).

Clientele with lower incomes were factored into risk groups (however, the models in this repository do not take this into account).

There are three different models that are hosted in this repository:
1. A Classical Cox Proportional-Hazards Model
2. An XGBoost Cox Model
3. A CatBoost Cox Model

# Model Evaluation
Each model was primarily evaluated by its Concordance Index (C-index). A C-index above 0.5 would indicate that the predictive power of the model means that the model's prediction was better than random chance. Out of theree models, the XGBoost model consistently performed the best.

# Why did XGBoost win?
In addition to having a C-index that was always above 0.5 (the highest I was able to achieve was about 0.65, which is above average but not substantially so), this model also had Brier score that was always close to 0. The Brier score indicates the accuracy of the model. After multiple re-tests, the highest Brier score was around 0.3. So why is this the case?
1. My parameters may be better fine tuned on the XGBoost model in comparison to the CatBoost model.
2. The amount of variables that are not at a categorical level are better on the model.
3. XGBoost could be handling overfitting, imputation, and other items better.
4. XGBoost appears to be doing regularization on the data a little better.

# Notes & Disclaimers
Working with synthetic data is tricky. It is very difficult to generate real world noise with artificial data. Therefore, these models will always inherently underperform (at first).
The models as they have been designed so far are not the most performant. Although I did perform good practices in their design (such as the feature engineering, grid search, etc.) they can be further improved. I will most likely come back to improve these models over time.

Here is a link that explains more about the purpose of Cox Models: https://datatab.net/tutorial/cox-regression
