<h1>Problem Statement</h1>
In 2018, $3.6 trillion was spent on health care in the United States, representing billions health insurance claims. It is an undisputed reality that some of these claims are fraudulent. Although they constitute only a small fraction, those fraudulent claims carry a very high price tag, both financially and in how they impact our perception of the integrity and value of our health care system.

The National Health Care Anti-Fraud Association (NHCAA) estimates that the financial losses due to health care fraud are in the tens of billions of dollars each year. A conservative estimate is 3% of total health care expenditures, while some government and law enforcement agencies place the loss as high as 10% of our annual health outlay, which could mean more than $300 billion.

Given the importance of this issue, I wanted to work on a project to try to predict potentially fraudulent claims from different providers.


<h2>Executive Summary</h2>
This project examines healthcare fraud, which is where a medical service claim is either completely fake, or a real claim is altered to reap greater payment from a medical insurance company to a provider such as a hospital or a clinic. Healthcare fraud can involve providers, doctors, patients, and even people within the insurance company itself. It can be the actions of an individual or the actions of a network. Healthcare fraud is difficult to identify, and medical insurers pay for fraud if it goes undiscovered. By exploring patterns in medical claims, fraud can be identified and addressed.

For this project, I imagined that I worked for a healthcare insurance company who wants to identify and flag potentially fraudulent providers, so that claims from those providers can undergo a review process. In order to do this, I needed to build a predictive machine learning algorithm to detect as much potential fraud as possible. As a secondary goal, I wanted to understand the factors that go into flagging a potentially fraudulent provider and generate insights into how those variables could be used in order to reduce costs for the health insurance firm. 
The data came in four CSV files containing patient and insurance claim information from mostly the year 2009, as well as a yes or no Potential Fraud flag. The combined dataframe has 56 features and over five hundred fifty thousand claims. Given the nature of the dataset, I needed to build a new dataframe with rows by provider rather than by rows by claim, because Potential Fraud was flagged by provider, not by claim. As a result, the features would also have to change orientation. To choose the best features for the Providers dataframe, I needed to do Exploratory Data Analysis (EDA) on the Claims dataframe.
The first model I tried was Logistic Regression, because I wanted to use the L1-norm penalty for two reasons: to explore the impact of each of the features I created and to gain insights into what features most strongly affect the classification. Lasso Logistic Regression reduced the coefficients from 87 down to 13. Then, Ridge Classifier was used to explore the reduced features; it better classified positive features, resulting in fewer false alarms.

Next, I wanted to explore a highly interpretable model, so I followed up with K-nearest Neighbors (KNN). This model scored the highest because it generated the fewest false negatives, however had about twice as many false positives as the other models.

For the same reasons I tried KNN, I attempted Gaussian Naive Bayes, or GNB. Gaussian Naive Bayes makes the assumption that all features are independent of each other, so we hoped it would highlight features considered less important to other models. However, GNB was my worst-performing model by a large margin.

I then explored Random Forest, because it is a more complex model than the previous three, captures non-linear relationships, and can be used for feature selection as well as gaining insights into which variables explain a flagged provider. Following Random Forest, I attempted Gradient Boosting, more difficult to tune and computationally more expensive. However, Gradient Boosting scored better than Random Forest and classified more accurately, especially false positives.

The last classifier I tried was Support Vector Machine (SVM) because it is not limited by the feature space of linear models and avoids the bias/variance tradeoff of non-linear models. SVM scored the same as Gradient Boosting, but had worse classification results.

In the end, most of my models fit well after parameter tuning and most of them had overall scores within hundreds of each other, indicating that the limitation in recall score was due to feature engineering, not the model choice or model tuning.

<h2>Software Requirements</h2>
<li><a href="https//www.numpy.org">Numpy</a></li>
<li><a href="https//www.pandas.pydata.org">Pandas</a></li>
<li><a href="https//www.scikit-learn.org">Scikit-learn</a></li>
<li><a href="https//www.seaborn.pydata.org">Seaborn</a></li>

<h2>Prerequisites</h2>
<li>Python version 3.0 and above</li>
<li>Jupyter notebook</li>

<h2>Project Directory</h2>
<u>code</u>
<li>1_Data_Cleaning.ipynb</li>
<li>2_EDA_and_Feature_Engineering.ipynb</li>
<li>3_Modelling_1st_iteration.ipynb</li>
<li>4_Modelling_2nd_iteration.ipynb</li>
