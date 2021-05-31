# Team 14 - Root-it: Optimization of Bidding Strategy for Online Ad Rankings

This repository contains notebooks analyzing the Root insurance data. The data contains information of customers who were presented advertisments from five insurance agencies, including the client. Each insurance company "bids" for the placement of their advertisement for each customer, and the ads are shown to the customer in order from highest to lowest bidder. The customer can then choose to click any ad shown and can purchase a policy from any ad they click.

The client has been using a flat $10 bid strategy for all customers and wants to use the data collected to optimize the efficiency of customer acquisition in future, while continuing to attract at least 400 customers for every 10,000.

The files are as follows:

Root_insuance_data.csv contains records of 10,000 customers including their information: current insurance status (insured, uninsured, or unknown), marital status (married, single), number of drivers (one, two, or three+), and number of vehicles (one or two+); whether the customer clicked the client's as; and whether the customer ultimately purchased a policy from the client.

Main_EDA.ipynb contains the initial exploratory data analysis, and explores both logistic regression and decision trees as methods to predict the probability that a given customer will choose to purchase a policy. Cross validation is used to determine that logistic regression may generalize better to future data. The data then analyzes the distribution of rankings for the client's $10 bids for different classes of customers.

Modeling.ipynb explains the approach for modeling the bids of competing insurance companies. The approach ultimately uses a mixture model of uniform distributions with exponential tails specific to each class of customer to model competing bids. The sear for the best bidding strategy is then formulated as a constrained optimization problem.

Optimize_Bids.ipynb calculates the minimum of expected cost per expected policy sold under the constraint that the expected number of policies equals 400 and computes the optimal bids for each customer using the mixture model, then finds the optimal bid strategy to meet 95% confidence greater than 400. In addition, it calculates the expected cost for 800 policies sold.

OptimizedBidsHybrid.csv contains the bid strategy obtained in 'Bids Hybrid and Cost.ipynb'

Gradient_Descent.ipynb implements a stochastic gradient descent to minimize the loss function, equal to the logarithm of expected cost per customer acquired plus a barrier function to force a solution with the constrained region. The variance is estimated through bootstrapping to find a confidence level that the constraint will be met with future data.

Gradient_Descent_Bids.csv contains the bids as a result of the stochastic gradient descent.
