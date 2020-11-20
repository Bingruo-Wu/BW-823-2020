## Welcome to Bingruo Wu's GitHub Pages

I am currently a second year master student studying statistical sciences at Duke University. This is a website I prepared for my big data class: BIOTSTAT823- 2020 Fall. In this page, I am going to describe how I finish my first assignment for this course: Start a personal website at Github Pages.

### Procedures

For starters, I created a new repository specifically used for this course and named as BW-823-2020 and chose to build it for public. Then I used the master branch as the root source for this website. After this, I used Jekyll as the blogging tool and chose to use Slate as the theme. 

### HW2

#### Problem 7: What is the 10001st prime

For this question, I checked whether a number is a prime number by checking if it is divisible by numbers <= it's square root, which is also the idea how I set up the anonymous function Lambda. Therefore, the 10001st prime for this question is 104743.

#### Problem 52: Permuted Multiples

I used the while loop to count how many iterations we need before reaching the smallest integer x, which makes 2x, 3x, 4x, 5x, and 6x, contain the same digits. Therefore, the final answer for this question is 142857.

#### Problem 80：Square root digital expansion

I first imported the decimal module to set the precision for this question to be 102, since we are aske to find the sum of the first one hundred decimal digits for the first one hundred natural numbers and all the square roots have to be irrational. Also, I seperated each digit and the decimal point by 'str()' and added digits at the left of the decimal with all at the right side. Therefore, the final answer for this question is 40886.

### HW3

### HW4

### HW5

### HW6

### HW7

### Final Project

In this final project, our team ('Doctor Covid') chose to use machine learning methods and techniques to model and predict the confirmed/death cases of COVID-19 in the US and total death number in the whole world.

#### Data source and description

Data is downloaded from Johns Hopkins University Center for Systems Science and Engineering Github repository(https://github.com/CSSEGISandData/COVID-19) and updated daily. JHU 

#### Models

For the model part, we have considered three types of modeling methods: Seasonal AutoRegressive Integrated Moving average(SARIMAX), Prophet and SVR.

There are two reasons that we think SARIMAX could be appropriate for the modeling. Frist, due to the property of dataset itself, which is scraped from JHU's repository and only contains date time and the value of dependent variables(confirmed/death cases), using time series models seems to be a reasonable choices. Second, in terms of the global death number, the dataset we are using to build a time series model is actually the daily increase data. This daily increase data is not consistent, but appear periodically, according to one trace plot. Thus, addding seasonality to our model is plausible. In the meantime, the first 3 of these 4 orders of SARIMAX are just seasonal versions of the ARIMA orders, which means we need to find a seasonal autoregressive order denoted by upper-case P, an order of seasonal integration denoted by upper-case D, and a seasonal moving average order signified by upper-case Q. Therefore, after multiple analysis work, we think SARIMAX(5,2,4)(0,0,0)[0] is the most appropriate model for predicting the global COVID-19 death case with MAE being 2347.05.

As for Prophet, an open source library that is published by Facebook, it has the ability to make good predictions for time series dataset, but works like a black box. The code and command are easy to use and the results are also pretty good. When using Prophet to predict the global death case, the MAE can be 1755.8, much less than using SARIMAX.

In terms of SVR, the idea is forecasting COVID-19′s confirmed/death/recover cases of the next 10 days by implementing SVM classification method. We applied this method to capture the predictor non-linearity and to improve the forecasting cases. In our case, we adopted polynomial kernel and use random-search cross-validation to find the best hyper-parameters. The training data is the time, and the label is confirmed cases. 

