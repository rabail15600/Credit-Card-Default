# Credit Card Default
 
As per the survey conducted by Worldpay, 40% of the point of sale (POS) payments in the USA in 2021 were settled
with credit cards. It is the most preferred payment method over other digital means (e.g. mobile wallet, BNPL, etc.).
Meanwhile, Federal Reserve notes that 83% of the people in the USA possess at least one credit card. With the
increasing usage of credit cards, the risk of users defaulting on payments is also on the rise.

Credit cards are a form of unsecured debt and represent a significant asset proportion of the banks. It is essential to
accurately assess risk before extending credit to avoid loss. In recent years, card users and the transaction volume has
mounted remarkably along with the delinquencies. As a solution, I have attempted to build a model that could help
financial institutions predict the individuals who would default on their credit card payments next month using clients’
private and financial information.

The dataset contains 24 columns and 30,000 rows for clients’ private information (sex, education level, marital status,
and age) and financial information (credit limit, repayment status, bill amount, and payment amount). The information
for repayment status, bill amount, and payment amount are provided for six months from April 2005 to September
2005. The target variable is a binary classification of whether the clients would default on next month’s credit card
payment or not (0 = no, 1 = yes). The dataset was collected to analyze the case of customers' default payments in
Taiwan.

As for the data preprocessing, the response variable, which is Default, had a proportion of 22% for 1s. Therefore, I
used stratified sampling to create balanced training, validation, and testing sets to ensure that the model is trained on
distributions representing the real-world case. Interestingly, the dataset had no missing values thus I did not perform
any type of imputation. However, upon running a check on the distribution of each numeric column, I found that
there are some extreme values in the attributes indicated by the dots spread outside the whiskers of the boxplots.
Therefore, I excluded four rows due to extreme values in bill_amt3, pay_amt2, and pay_amt3. I encoded sex,
education, marriage, default, and repayment status for six months (pay_1 to pay_6) as categorical variables. I also
tuned their labels for clarity. To capture maximum information from the dataset for useful modeling, I also engineered
new features that highlighted the differential amount for exceeding the limit and the percentage of the bill paid for
each month.

With regards to model building, I built a total of five classification models to predict credit card defaults including
logistic regression, decision tree, boosted trees, bootstrap forest, and neural network. In terms of the test model
comparison, I consider the decision tree as the best model. The total accuracy rate of pruned decision trees with 6
number splits stands at 82% which is similar to other models. The precision and specificity are 70% and 96%, which
are also better than most other models. However, the sensitivity is slightly lower at 33% versus an average of 34% in
other models. Meanwhile, the root absolute squared error is 0.37 which is similar to other models tried and tested.
The AUC and R-Squared turn out to be 0.75 and 17%. In the tree, the root node where the best split occurs is pay_1.
The rationale behind recommending this model is that it has the built-in variable selection and has no assumptions of
linear relationship thus, it is easy to use. Importantly, it is a white-box model. If a given situation is observable in a
model, the explanation for the condition is easily explained by Boolean logic.

It is not only sufficient to recommend the model without identifying its use cases, therefore, I will be recommending
some actions that could be taken. The most important variables to predict credit card default include pay_1, pay_2,
education levels, and credit limit. Most often, users with lower credit card limits tend to be delinquent therefore, the
banks can establish more stringent requirements for the issuance of credit cards even with a lower limit. Interestingly,
individuals aged between 25 and 30 are more likely to default. Perhaps, they are more aggressive spenders thus, they
should be subject to rigorous inspection prior to extending credit. Based on the model predictions, financial
institutions can take credit card management measures (e.g. reminders) targeted at people that are likely to default.
