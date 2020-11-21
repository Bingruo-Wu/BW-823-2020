## Welcome to Bingruo Wu's GitHub Pages

I am currently a second year master student studying statistical sciences at Duke University. This is a website I prepared for my big data class: BIOTSTAT823- 2020 Fall, where I show all my work for this course, enjoy!

### HW1: Explain the procedures to buid a personal website through Github Pages

For starters, I created a new repository specifically used for this course and named as BW-823-2020 and chose to build it for public. Then I used the master branch as the root source for this website. After this, I used Jekyll as the blogging tool and chose to use Slate as the theme. 

### HW2

#### P7: What is the 10001st prime

For this question, I checked whether a number is a prime number by checking if it is divisible by numbers <= it's square root, which is also the idea how I set up the anonymous function Lambda. Therefore, the 10001st prime for this question is 104743.

#### P52: Permuted Multiples

I used the while loop to count how many iterations we need before reaching the smallest integer x, which makes 2x, 3x, 4x, 5x, and 6x, contain the same digits. Therefore, the final answer for this question is 142857.

#### P80：Square root digital expansion

I first imported the decimal module to set the precision for this question to be 102, since we are aske to find the sum of the first one hundred decimal digits for the first one hundred natural numbers and all the square roots have to be irrational. Also, I seperated each digit and the decimal point by 'str()' and added digits at the left of the decimal with all at the right side. Therefore, the final answer for this question is 40886.

### HW3: Visulizations

See the HW3 Jupyter Notebook for all the visualizations.

### HW4: Spotify Song

#### 1NF

I started by cleaning the dataset, like making sure ther are no duplications for all the rows and columns and all the cells only contain one element. I also did some transformation for the data and tried to make the dataset cleaner, like tranlating 'duration_ms'into 'duration_min' and removing the unnecessary part in the name.

#### 2NF

For the second normal form, I noticed that some variales describe the attributes of the song, while others describe album and playlist. So I divided the table into three parts: 'Song', 'Album' and 'Playlist' and then dropped duplicates of all these three.

#### 3NF

For the Playlist Table, there is a relationship between the 'playlist_genre' and 'playlist_subgenre', so another table is created to store this the relationship between genre and subgenre.


### HW5: Star Wars

For this question, I looped from 1 to 100 for “people” and 1 to 10 for “film” and I filtered the result by checking the json file. For the people data, we have 82 valid data points and 6 valid data points for the film data.

#### Finding the oldest character

Yoda is the oldest.

#### Films that Yoda was on

The Empire Strikes Back, Return of the Jedi, The Phantom Menace, Attack of the Clones, Revenge of the Sith, 2020 Ink theme on Hugo


### HW6: PhDs awarded in the US

I firstly used melt and concat function in pandas to change the data from the wide to long. The specific steps can be found in the hw6.ipynb file.


### Final Project:

For this final project, our team ('Doctor Covid') chose to use machine learning methods and techniques to model and predict the confirmed/death cases of COVID-19 in the US and total death number in the whole world.

#### Data source and description

Data is downloaded from Johns Hopkins University Center for Systems Science and Engineering Github repository(https://github.com/CSSEGISandData/COVID-19) daily, which only contains the dependent variables we want to model(confirmed/death/recover cases) and time.

#### Model Attempts

For the model part, we have considered three types of modeling methods: Seasonal AutoRegressive Integrated Moving average(SARIMAX), Prophet and SVR.

There are two reasons that we think SARIMAX could be appropriate for the modeling. Frist, due to the property of dataset itself, which is scraped from JHU's repository and only contains date time and the value of dependent variables(confirmed/death cases), using time series models seems to be a reasonable choices. Second, in terms of the global death number, the dataset we are using to build a time series model is actually the daily increase data. This daily increase data is not consistent, but appear periodically, according to one trace plot. Thus, addding seasonality to our model is plausible. In the meantime, the first 3 of these 4 orders of SARIMAX are just seasonal versions of the ARIMA orders, which means we need to find a seasonal autoregressive order denoted by upper-case P, an order of seasonal integration denoted by upper-case D, and a seasonal moving average order signified by upper-case Q. Therefore, after multiple analysis work, we think SARIMAX(5,2,4)(0,0,0)[0] is the most appropriate model for predicting the global COVID-19 death case with MAE being 2347.05.

As for Prophet, an open source library that is published by Facebook, it has the ability to make good predictions for time series dataset, but works like a black box. The code and command are easy to use and the results are also pretty good. When using Prophet to predict the global death case, the MAE can be 1755.8, much less than using SARIMAX.

In terms of SVR, the idea is forecasting COVID-19′s confirmed/death/recover cases of the next 10 days by implementing SVM classification method. We applied this method to capture the predictor non-linearity and to improve the forecasting cases. In our case, we adopted polynomial kernel and use random-search cross-validation to find the best hyper-parameters. The training data is the time, and the label is confirmed cases.

#### Results

From the SVR plot, we can see that SVR is quite accurate on predicting confirm cases and recover cases. However, for death cases there is some gap between the predicted and the actual data. One reason could be we tune the hyper-parameter by training the confirm datasets, and use that parameter for all three predict models. Tuning parameters take a long time to search the best ones, and for saving some time, we decided to use that for all SVR models. Such parameter is optimized for the confirm cases, but not necessary the best for death cases.

SARIMAX and Prophet are uesd to predict global death cases, which performs well for data before the end of October，but when predict the global death number in November, they both underfit. However, Prophet tends to perform better with smaller MAE.

