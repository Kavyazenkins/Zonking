# Zonking
Boston project
metadata": {},
   "source": [
    "## Getting Started\n",
    "In this project, you there will be evaluated the performance and predictive power of a model that has been trained and tested on data collected from homes in suburbs of Boston, Massachusetts. A model trained on this data that is seen as a *good fit* could then be used to make certain predictions about a home — in particular, its monetary value. This model would prove to be invaluable for someone like a real estate agent who could make use of such information on a daily basis.\n",
    "In this project, there will be evaluated the performance and predictive power of a model that has been trained and tested on data collected from homes in suburbs of Boston, Massachusetts. A model trained on this data that is seen as a *good fit* could then be used to make certain predictions about a home — in particular, its monetary value. This model would prove to be invaluable for someone like a real estate agent who could make use of such information on a daily basis.\n",
    "\n",
    "The dataset for this project originates from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Housing). The Boston housing data was collected in 1978 and each of the 506 entries represent aggregated data about 14 features for homes from various suburbs in Boston, Massachusetts. For the purposes of this project, the following preprocessing steps have been made to the dataset:\n",
    "- 16 data points have an `'MEDV'` value of 50.0. These data points likely contain **missing or censored values** and have been removed.\n",
@@ -142,27 +142,18 @@
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Question 1 - Feature Observation\n",
    "## Feature Observation\n",
    "\n",
    "As a reminder, we are using three features from the Boston housing dataset: `'RM'`, `'LSTAT'`, and `'PTRATIO'`. For each data point (neighborhood):\n",
    "- `'RM'` is the average number of rooms among homes in the neighborhood.\n",
    "- `'LSTAT'` is the percentage of homeowners in the neighborhood considered \"lower class\" (working poor).\n",
    "- `'PTRATIO'` is the ratio of students to teachers in primary and secondary schools in the neighborhood.\n",
    "\n",
    "\n",
    "** Using your intuition, for each of the three features above, do you think that an increase in the value of that feature would lead to an **increase** in the value of `'MEDV'` or a **decrease** in the value of `'MEDV'`? Justify your answer for each.**\n",
    "\n",
    "**Hint:** This problem can phrased using examples like below.  \n",
    "* Would you expect a home that has an `'RM'` value(number of rooms) of 6 be worth more or less than a home that has an `'RM'` value of 7?\n",
    "* Would you expect a neighborhood that has an `'LSTAT'` value(percent of lower class workers) of 15 have home prices be worth more or less than a neighborhood that has an `'LSTAT'` value of 20?\n",
    "* Would you expect a neighborhood that has an `'PTRATIO'` value(ratio of students to teachers) of 10 have home prices be worth more or less than a neighborhood that has an `'PTRATIO'` value of 15?"
    "- `'PTRATIO'` 
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Answer: **\n",
    "\n",
    "Intuitively, for each feature I would predict the following:\n",
    "\n",
    "    - Houses with more rooms (higher 'RM' value) will be worth more. Usually houses with more rooms are bigger and can fit more people, so it is reasonable that they cost more money. They are directly proportional variables.\n",
@@ -179,21 +170,17 @@
    "----\n",
    "\n",
    "## Developing a Model\n",
    "In this second section of the project, you will develop the tools and techniques necessary for a model to make a prediction. Being able to make accurate evaluations of each model's performance through the use of these tools and techniques helps to greatly reinforce the confidence in your predictions."
    "In this second section of the project, I will develop the tools and techniques necessary for a model to make a prediction. Being able to make accurate evaluations of each model's performance through the use of these tools and techniques helps to greatly reinforce the confidence in your predictions."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Implementation: Define a Performance Metric\n",
    "It is difficult to measure the quality of a given model without quantifying its performance over training and testing. This is typically done using some type of performance metric, whether it is through calculating some type of error, the goodness of fit, or some other useful measurement. For this project, you will be calculating the [*coefficient of determination*](http://stattrek.com/statistics/dictionary.aspx?definition=coefficient_of_determination), R<sup>2</sup>, to quantify your model's performance. The coefficient of determination for a model is a useful statistic in regression analysis, as it often describes how \"good\" that model is at making predictions. \n",
    "It is difficult to measure the quality of a given model without quantifying its performance over training and testing. This is typically done using some type of performance metric, whether it is through calculating some type of error, the goodness of fit, or some other useful measurement. For this project, you I ill be calculating the [*coefficient of determination*](http://stattrek.com/statistics/dictionary.aspx?definition=coefficient_of_determination), R<sup>2</sup>, to quantify the model's performance. The coefficient of determination for a model is a useful statistic in regression analysis, as it often describes how \"good\" that model is at making predictions. \n",
    "\n",
    "The values for R<sup>2</sup> range from 0 to 1, which captures the percentage of squared correlation between the predicted and actual values of the **target variable**. A model with an R<sup>2</sup> of 0 is no better than a model that always predicts the *mean* of the target variable, whereas a model with an R<sup>2</sup> of 1 perfectly predicts the target variable. Any value between 0 and 1 indicates what percentage of the target variable, using this model, can be explained by the **features**. _A model can be given a negative R<sup>2</sup> as well, which indicates that the model is **arbitrarily worse** than one that always predicts the mean of the target variable._\n",
    "\n",
    "For the `performance_metric` function in the code cell below, you will need to implement the following:\n",
    "- Use `r2_score` from `sklearn.metrics` to perform a performance calculation between `y_true` and `y_predict`.\n",
    "- Assign the performance score to the `score` variable."
    "The values for R<sup>2</sup> range from 0 to 1, which captures the percentage of squared correlation between the predicted and actual values of the **target variable**. A model with an R<sup>2</sup> of 0 is no better than a model that always predicts the *mean* of the target variable, whereas a model with an R<sup>2</sup> of 1 perfectly predicts the target variable. Any value between 0 and 1 indicates what percentage of the target variable, using this model, can be explained by the **features**. _A model can be given a negative R<sup>2</sup> as well, which indicates that the model is **arbitrarily worse** than one that always predicts the mean of the target variable._"
   ]
  },
  {
@@ -217,84 +204,12 @@
    "    return score"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Question 2 - Goodness of Fit\n",
    "Assume that a dataset contains five data points and a model made the following predictions for the target variable:\n",
    "\n",
    "| True Value | Prediction |\n",
    "| :-------------: | :--------: |\n",
    "| 3.0 | 2.5 |\n",
    "| -0.5 | 0.0 |\n",
    "| 2.0 | 2.1 |\n",
    "| 7.0 | 7.8 |\n",
    "| 4.2 | 5.3 |\n",
    "\n",
    "Run the code cell below to use the `performance_metric` function and calculate this model's coefficient of determination."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Model has a coefficient of determination, R^2, of 0.923.\n"
     ]
    }
   ],
   "source": [
    "# Calculate the performance of this model\n",
    "score = performance_metric([3, -0.5, 2, 7, 4.2], [2.5, 0.0, 2.1, 7.8, 5.3])\n",
    "print(\"Model has a coefficient of determination, R^2, of {:.3f}.\".format(score))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* Would you consider this model to have successfully captured the variation of the target variable? \n",
    "* Why or why not?\n",
    "\n",
    "** Hint: **  The R2 score is the proportion of the variance in the dependent variable that is predictable from the independent variable. In other words:\n",
    "* R2 score of 0 means that the dependent variable cannot be predicted from the independent variable.\n",
    "* R2 score of 1 means the dependent variable can be predicted from the independent variable.\n",
    "* R2 score between 0 and 1 indicates the extent to which the dependent variable is predictable. An \n",
    "* R2 score of 0.40 means that 40 percent of the variance in Y is predictable from X."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Answer:**\n",
    "\n",
    "Yes, this model succesfully captured the variation of the target variable. There are two reasons why I believe this:\n",
    "\n",
    "- First, if we take a look at the values (True and Predicted) we can see that the deviations between them are low.\n",
    "\n",
    "- In addition, when computing the R^2 score, we have obtained a value of 0.923, which is quite closely to 1. As this R^2 score is the proportion of the dependent variable that can be predicted from the independent variable, by a linar model, and it is quite high, we conclude that our model has made quite good predictions.\n",
    "\n",
    "R-squared = Explained variation/Total variation"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Implementation: Shuffle and Split Data\n",
    "Your next implementation requires that you take the Boston housing dataset and split the data into training and testing subsets. Typically, the data is also shuffled into a random order when creating the training and testing subsets to remove any bias in the ordering of the dataset.\n",
    "\n",
    "For the code cell below, you will need to implement the following:\n",
    "- Use `train_test_split` from `sklearn.model_selection` to shuffle and split the `features` and `prices` data into training and testing sets.\n",
    "  - Split the data into 80% training and 20% testing.\n",
    "  - Set the `random_state` for `train_test_split` to a value of your choice. This ensures results are consistent.\n",
    "- Assign the train and testing splits to `X_train`, `X_test`, `y_train`, and `y_test`."
    "For the next implementation it is required to take the Boston housing dataset and split the data into training and testing subsets. Typically, the data is also shuffled into a random order when creating the training and testing subsets to remove any bias in the ordering of the dataset."
   ]
  },
  {
@@ -325,19 +240,17 @@
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Question 3 - Training and Testing\n",
    "### Training and Testing\n",
    "\n",
    "* What is the benefit to splitting a dataset into some ratio of training and testing subsets for a learning algorithm?\n",
    "You may ask now:\n",
    "\n",

    "* What is t 3endit of splitting btw the he benefit to splitting a dataset into some ratio of training and testing subsets for a learning algorithm?"
 areas of the repository  ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Answer: **\n",
    "\n",
    "It is useful to evaluate our model once it is trained. We want to know if it has learned properly from a training split of the data. There can be 3 different situations:\n",
    "\n",
    "1) The model didn´t learn well on the data, and can't predict even the outcomes of the training set, this is called underfitting and it is caused because a high bias.\n",
@@ -354,17 +267,15 @@
    "----\n",
    "\n",
    "## Analyzing Model Performance\n",
    "In this third section of the project, you'll take a look at several models' learning and testing performances on various subsets of training data. Additionally, you'll investigate one particular algorithm with an increasing `'max_depth'` parameter on the full training set to observe how model complexity affects performance. Graphing your model's performance based on varying criteria can be beneficial in the analysis process, such as visualizing behavior that may not have been apparent from the results alone."
    "In this third section of the project, we'll take a look at several models' learning and testing performances on various subsets of training data. Additionally, we'll investigate one particular algorithm with an increasing `'max_depth'` parameter on the full training set to observe how model complexity affects performance. Graphing the model's performance based on varying criteria can be beneficial in the analysis process, such as visualizing behavior that may not have been apparent from the results alone."
   ]
