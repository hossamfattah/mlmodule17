# What drives the price of a car

# Deliverables

The Jupyter notebook is available here:
[Jupyter Notebook](https://github.com/hossamfattah/mlmodule11/blob/3bd6deaa9dca0e72a0f3857b30e101409c2af454/MyWorkF.ipynb)


# Discussion
I read the dataset and started to explore it. I used info() to see what columns and data types is each column

`0   id            426880 non-null  int64

 1   region        426880 non-null  object
 
 2   price         426880 non-null  int64
 
 3   year          425675 non-null  float64
 
 4   manufacturer  409234 non-null  object
 
 5   model         421603 non-null  object
 
 6   condition     252776 non-null  object
 
 7   cylinders     249202 non-null  object
 
 8   fuel          423867 non-null  object
 
 9   odometer      422480 non-null  float64
 
 10  title_status  418638 non-null  object
 
 11  transmission  424324 non-null  object
 
 12  VIN           265838 non-null  object
 
 13  drive         296313 non-null  object
 
 14  size          120519 non-null  object
 
 15  type          334022 non-null  object
 
 16  paint_color   296677 non-null  object
 
 17  state         426880 non-null  object`
 

I noticed 'cylinders' column can be converted to numeric column after removing the substring "cylinders". I did that and converted 'cylinders' into numeric column

To understand data, I plotted histogram of different numeric features. 

This is by price

![Screenshot](./images/HistPrice.png)


This is by year

![Screenshot](./images/HistYear.png)


This is by odometer

![Screenshot](./images/HistOdometer.png)


The corrleation of each feature to the target price is also listed below

![Screenshot](./images/corr01.png)


This is the histogram by car manufacturer
![Screenshot](./images/carsByManuf.png)


This is a scatter plot of price by fuel from different manufacturers
![Screenshot](./images/carsByFuel.png)


his is a scatter plot of price by odometer. It shows prices icreases with decreasing odometer
![Screenshot](./images/carsByOdometer.png)


I started using linear regression model and polynomial with each of the numeric features and calculated MSE.

This is linear regression model with varying polynomial degrees for features: 
**'odometer'**

and target 'price'

![Screenshot](./images/MSE_odometer.png)


This is linear regression model with varying polynomial degrees for features: 'cylinders' and target 'price'

![Screenshot](./images/MSE_cylinders.png)


This is linear regression model with varying polynomial degrees for features: 

**'odometer','year','cylinders' **

and target 'price'

![Screenshot](./images/MSE_lr.png)


There are many non-numeric features in the dataset (catogiral features). I used on-hot encoder and converted all of them to the following ( i excluded very few columns which are not relevenat to price such as VIN):

![Screenshot](./images/ohenc.png)


Then, I used a linear regression model with varying polynomial degrees and standard scaler for 
features: 

**'fuel_diesel','type_truck','size_full-size','drive_4wd', 'odometer','year','cylinders'**

and target 'price'

I choosed those features because they are the highly corrlated features with the target.

![Screenshot](./images/MSE_lr_ss_poly.png)


Then, I used a linear regression model with varying polynomial degrees and standard scaler for all features (all columns in the dataset)
target 'price'

![Screenshot](./images/MSE_lr_ss_poly_all.png)


I used Ridge model with standard scaler. These are the top 10 features:

score: 0.4128668886714879

year     0.111 +/- 0.003

fuel_diesel 0.065 +/- 0.001

odometer 0.042 +/- 0.001

size_full-size 0.022 +/- 0.001

type_sedan 0.020 +/- 0.001

cylinders 0.015 +/- 0.001

transmission_manual 0.015 +/- 0.001

condition_like new 0.013 +/- 0.001

transmission_other 0.013 +/- 0.001

drive_fwd 0.012 +/- 0.001



I used Linear regression with a sequential feature selector. These are the top features:

score: 0.41998455654300393

year     869004992939.205 +/- 5811335957.860

transmission_other 176762591382.147 +/- 1040363181.065

cylinders 104150982230.724 +/- 663169015.500

size_full-size 100341633413.173 +/- 499405088.626

condition_like new 90566097673.554 +/- 749266698.610

drive_fwd 77466685540.497 +/- 577141472.968

manufacturer_ferrari 50026094302.668 +/- 294661711.916

manufacturer_porsche 2801015399.137 +/- 400.899

fuel_diesel-0.000 +/- 0.000


I used Lasso regression with a sequential feature selector. These are the top features:

score: 0.4198008175424963

cylinders 0.00115504 +/- 0.00017993

manufacturer_porsche 0.00035559 +/- 0.00012828

transmission_other 0.00013212 +/- 0.00006795

condition_like new 0.00011683 +/- 0.00006791

size_full-size 0.00010375 +/- 0.00006202

year     0.00003070 +/- 0.00003704

fuel_diesel 0.00000000 +/- 0.00000000

drive_fwd 0.00000000 +/- 0.00000000

manufacturer_ferrari 0.00000000 +/- 0.00000000

I used Lasso regression with a sequential feature selector and polynomial degree of 2. These are the top features:

score: 0.4198008175424963

fuel_diesel 0.11883588 +/- 0.00213299

year     0.11198753 +/- 0.00263502

odometer 0.04135759 +/- 0.00137010

type_sedan 0.03336416 +/- 0.00116645

condition_like new 0.02451925 +/- 0.00120265

type_SUV 0.02360657 +/- 0.00098519

size_full-size 0.02292873 +/- 0.00070670

transmission_other 0.02282619 +/- 0.00102234

manufacturer_ferrari 0.01710308 +/- 0.00093846

cylinders 0.01440978 +/- 0.00071329


I also used PCA with three components and I did clustering. I see there is a clear grouping:



![Screenshot](./images/Cluster.png)


# Summary

In the above, We analyzed a dataset for car priced based on many features. The features are big in numbers and we used different techniques or models to analyze and study which features affects the car price the most. 
We used many models of varying complexities. We used the pairwise autocorrelation to see which feature is highly correlated with the car price. We used linear regression, Ridge, Lasso and with different polynomial degrees and standard scaler. 

We cross-validated each model and find the mean square error for the training and test datasets. We listed the important features given by each model. 

We also used Principal component Analysis (PCA) and grouped the data into three distinguished groups.

# Recommendations

1- The number of features is huge that can influence car prices. Based on our findings and models, we find the following features give a good estimate and prediction of car price: 

**fuel_diesel, type_truck , size_full-size, drive_4wd, odometer, year, cylinders**

2- All models used agree on the following features as big influencer of car price. Thus, car dealers can depend on these features to estimate car price: 

**size_full-size, year, cylinders**

3- In addition, the following two features can be used as well: 

**fuel_diesel, odometer**


