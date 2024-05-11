# Diamond-Predictor

# Introduction
The 4Cs: cut, clarity, color, and carat weight, are internationally accepted standards for assessing the quality of a diamond. Diamond cut grade is a pivotal factor in determining the beauty and value of a diamond.

The dataset being used reports on the characteristics of diamonds. We want to use the KNN classification method to predict the cut grades of diamonds.

The columns of the dataset:

carat: a unit of measurement for a diamond's weight.
cut: cut grades of diamonds, measured in five scales (high to low): Ideal, Premium, Very good, Good, Fair.
color: color is graded on a scale from D (colorless) to Z (light yellow or brown).
clarity: the presence of internal and external flaws within a diamond.
depth: the distance from the table to the culet (the bottom of the diamond).
table: the flat, topmost facet of diamonds.
price: The price of diamonds.
x: the x-dimension of diamonds.
y: the y-dimension of diamonds.
z: the z-dimension of diamonds.

# Method Overview
Our project wishes to identify whether we can use diamond data to predict the cut of a diamond.

- Preliminary Exploratory Data Analysis: Prepare our dataset by reading and wrangling for further analysis.
- Splitting Data: Split the filtered dataset into a testing and training set. Summarize the distribution of each categorical predictor variables for the training data.
- Select Predictor Variables: Check for the relationship between each variable and the cut quality. Eliminate the variables with no visible correlation.
- Create a Classification Model: Employ the K-nearest neighbors classification algorithm to identify the optimal K value. After identifying the most suitable value, run the model on the test set to check the accuracy value.
- Fulfill curiousity by checking whether the addition of predictor variables increases or decreases the accuracy of predictions. We will do this by adding predictor variables to our recipe, then running that model on the test set to check the accuracy value.

# Splitting Data
**Splitting the data into training and testing data**
We have 53940 recorded observations that can be used for analysis. Our next step is to split the data into a training and testing set. We set the proportion to 0.75, this means 75% of our 53940 observations will be used towards the training set, and the remaining observations will be stored for the testing set. We set our seed to 2023 to create replicable randomized results.

**Selecting Predictors**
The plots below are used to select the predictors based on effectiveness to prediction. We can observe the box plots and select those that exhibit some type of relationship with the cut quality.

<img width="645" alt="Screenshot 2024-05-10 at 6 14 11 PM" src="https://github.com/atao2004/Diamond-Predictor/assets/148929819/f06ef6e9-ad64-42ce-a60a-68f47e2cb453">

# Building a Classification Model

First, let's choose a reasonable k value to work with. We use tuning to select the best k value, and use cross validation to make sure the accuracy is not an unlucky value.

**Creating a recipe**

Our first step in building the classification model is to create a recipe so our training data can be prepared to be used in the model. We included both the scale and center functions to ensure all our predictor variables have a mean of zero and standard deviation of one to ensure a bell curve distribution.
# Summary Of Results

<img width="497" alt="Screenshot 2024-05-10 at 6 26 08 PM" src="https://github.com/atao2004/Diamond-Predictor/assets/148929819/45c3aa46-f47e-4b4a-bb0a-9ae7286a3afe">

Through this data analysis, it was found that some of the geometry factors, the depth and table, are the main two quantitative predictors that can be used to predict the cut quality of diamonds. When the model ran with those two being used as predictors, it was found that the accuracy of the prediction is 70.8%. The model was then tested again but this time, with the remaining geometry factors x,y,z added as the predictors, the accuracy was increased to 72.7% (1.9% accuracy increase). The main takeaway from this finding is that while geometric factors affect the overall visual aesthetic of the diamond, some of them might not have a very significant impact on the cut quality prediction.


<img width="1023" alt="Screenshot 2024-05-10 at 6 22 41 PM" src="https://github.com/atao2004/Diamond-Predictor/assets/148929819/d907fe20-39f6-4f2c-b0e3-870fe1e9a680">
