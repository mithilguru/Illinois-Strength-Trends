# Illinois-Strength-Trends
## Project Overview
* Analyzed Illini Men's Gymnastics strength test data collected on Hawkin
* Performed correlation and regression analysis to select key variables influencing test performance

## Intro
A collaborative venture with coach Mike Freeze of the University of Illinois, this is an in-depth analysis of the Illini Men's Gymnastics athletes' strength test performance over summer training camp in July 2023. Focusing on two tests, Drop Jumps and Isometric Mid-Thigh Pulls, we leveraged the Hawkin Dynamics system to gather multifaceted data beyond force output to better understand strength trends over time and develop actionable training recommendations to elevate athletic performance for important meets. 

In this initial analysis, the emphasis is on identifying influential variables in the dataset that predict the key metrics of the tests, aiming to better recognize signs of strain or over-training among athletes.

## EDA

### Data

**Drop Jump Measures and Variables** 

The drop jump test is designed to test reactivity. The athlete begins by standing on a platform behind the force plates, stepping off and dropping onto the plates, absorbing the drop and immediately leaping again. The goal is to measure how fast the athlete shifts from force absorption to propulsion. Target metrics include Jump Height and Reactive Strength Index (RSI).

The variables can be categorized into phases of the test -

Identifiers 

* `TestId`
* `Date`
* `Time`
* `Name`
* `Type`


DROP Phase - lasts from test start until athlete contacts the plates

General Measurements

* `System Weight`
* `Drop Height`
* `Jump Height`

Braking phase - begins immediately after contact with plates. Consists of athlete loading force onto their legs in preparation for taking off (eccentric)

* Braking Force -  `Avg. Braking Force`, `Avg. Relative Braking Force`, `Avg. Braking RFD`, `Left Avg. Braking RFD`, `Right Avg. Braking RFD`, `L|R Peak Braking Force`, `L|R Avg. Braking Force`, `L|R Avg. Braking RFD`, `Right Force at Peak Braking Force`, `Left Force at Peak Braking Force`, `Time to Peak Braking Force`
* Braking Impulse - `Braking Impulse`, `Relative Braking Impulse`, `Braking Net Impulse`, `Relative Braking Net Impulse`, `L|R Braking Impulse Index`
* Braking Velocity - `Avg. Braking Velocity`
* Braking Power - `Avg. Braking Power`, `Avg. Relative Braking Power`, `Peak Braking Power`, `Peak Relative Braking Power`
* Braking Phase Timing - `Braking Phase`, `Braking Phase %`

Propulsive phase - starts when velocity hits 0 on the plates and continues until the athlete takes off (concentric)

* Propulsive Force - `Avg. Propulsive Force`, `Avg. Relative Propulsive Force`, `L|R Peak Propulsive Force`, `L|R Avg. Propulsive Force`
* Propulsive Impulse - `Propulsive Impulse`, `Relative Propulsive Impulse`, `Propulsive Net Impulse`, `Relative Propulsive Net Impulse`, `L|R Propulsive Impulse Index`
* Propulsive Velocity - `Avg. Propulsive Velocity`
* Propulsive Power - `Avg. Propulsive Power`, `Avg. Relative Propulsive Power`, `Avg. Relative Propulsive Power`, `Peak Relative Propulsive Power`
* Propulsive Phase Timing - `Propulsive Phase`, `Propulsive Phase %`
* `Time to Takeoff`
* `Contact Time`
* Reactive Strength Index - `mRSI`, `RSI`

Flight phase - segment of the test for which athlete is airborne after the drop jump

* `Takeoff Velocity`
* `Flight Time`

Landing phase - athlete lands back on the plate after the jump

* Landing Force - `Avg. Landing Force`, `Relative Peak Landing Force`, `L|R Peak Landing Force`, `L|R Avg. Landing Force`, `Left Force at Peak Landing Force`, `Right Force at Peak Landing Force`
* Landing Impulse - `L|R Landing Impulse Index`

Stability

* `Impact Peak`
* `Stiffness`
* `Spring Like Correlation`
* `Countermovement Depth`
* `Jump Momentum`

Other

* `Segment`
* `Position`
* `Excluded`
* `Tags`

**Isometric Test Measures and Variables**

The isometric mid-thigh pull test is designed to measure absolute force production, as research shows max isometric force is greater than max concentric force production. The test is set up with the athlete on the force plates gripping the bar. They then pull the bar to mid-thigh height and hold the position for 3 seconds. To measure how rapidly the athlete can reach max force, target metrics such as Rate of Force Development (RFD) are considered alongside Peak Force.

The measures are divided into 50ms phases - 

Identifiers

* `TestId`
* `Date`
* `Time`
* `Name`

General Measurements 

* `System Weight`
* `Length of Pull`

Force

* Peak Force - `Peak Force`, `Net Peak Force`, `Relative Peak Force`, `Relative Peak Force (BW)`, `L|R Peak Force`, `Left Peak Force`, `Right Peak Force`
* Force at 0 ms - `Force at 0 ms`, `Net Force at 0 ms`, `Relative Force at 0 ms`, `Relative Force at 0 ms (BW)`, `Left Force at 0 ms`, `Right Force at 0 ms`
* Force at 50 ms - `Force at 50 ms`, `Net Force at 50 ms`, `Relative Force at 50 ms`, `Relative Force at 50 ms (BW)`, `Left Force at 50 ms`, `Right Force at 50 ms`
* Force at 100 ms - `Force at 100 ms`, `Net Force at 100 ms`, `Relative Force at 100 ms`, `Relative Force at 100 ms (BW)`, `Left Force at 100 ms`, `Right Force at 100 ms`
* Force at 150 ms - `Force at 150 ms`, `Net Force at 150 ms`, `Relative Force at 150 ms`, `Relative Force at 150 ms (BW)`, `Left Force at 150 ms`, `Right Force at 150 ms`
* Force at 200 ms - `Force at 200 ms`, `Net Force at 200 ms`, `Relative Force at 200 ms`, `Relative Force at 200 ms (BW)`, `Left Force at 200 ms`, `Right Force at 200 ms`
* Force at 250 ms - `Force at 250 ms`, `Net Force at 250 ms`, `Relative Force at 250 ms`, `Relative Force at 250 ms (BW)`, `Left Force at 250 ms`, `Right Force at 250 ms`

Rate of Force Development and Impulse

* `Time to Peak Force`
* RFD 0-50 ms - `RFD 0-50 ms`, `Impulse 0-50ms`, `Net Impulse 0-50ms`
* RFD 0-100 ms - `RFD 0-100 ms`, `Impulse 0-100ms`, `Net Impulse 0-100ms`
* RFD 0-150 ms - `RFD 0-150 ms`, `Impulse 0-150ms`, `Net Impulse 0-150ms`
* RFD 0-200 ms - `RFD 0-200 ms`, `Impulse 0-200ms`, `Net Impulse 0-200ms`
* RFD 0-250 ms - `RFD 0-250 ms`, `Impulse 0-250ms`, `Net Impulse 0-250ms`

Other

* `Initiation Threshold`
* `Segment`
* `Position`
* `Excluded`
* `Tags`

### Analysis

Visualizing the team progress in the target metrics for each test:

**Drop Jump** - `Jump Height`, `RSI`

**Isometric Test** - `Peak Force`, `Peak RFD`

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/JumpHeight.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RSI.png)

Observing mean `Jump Height` and `RSI` over testing dates shows the athletes' performance generally peaked at the start of July, though RSI recovered to near-peak levels by the end of the month.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/PeakForce.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RFD.png)

For the Isometric Test, there is no default measure for rate of peak force development, so I've created a column that calculates this (`Peak RFD` = `Peak Force` / `Time to Peak Force`).
Viewing mean `Peak Force` and `RFD`, both spike in mid-July and late July, but remain mostly constant throughout the duration of the training program.

I'll be analyzing correlations to see if there are any strong linear relationships between feature types.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/JumpHeight-Correlations.png)

The strongest linear associations to `Jump Height` are measures relating to propulsion (i.e. `Takeoff Velocity`, Propulsive Impulse, Velocity, Power, `Jump Momentum`, `Spring Like Correlation`). 

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RSI-Correlations.png)

For `RSI`, measures relating to force timings have the strongest linear associations (i.e. `Avg. Braking RFD`, `Time to Takeoff`, as well as `Stiffness`). `Contact Time` was not included since RSI is calculation of Jump Height over Contact Time.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/PeakForce-Correlations.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RFD-Correlations.png)

When viewing `Peak Force` and `RFD` correlations, checking for just strong linear relationships did not reveal much, so the range of top correlation was expanded. For both variables, maintaining strong force at the later stages of the lift (150-250ms) is a good predictor for overall peak force and RFD. Right force is also predictably higher than left force in predicting total force output (standard dominant side imbalances).

Now I'll build baseline models to predict the target metrics. By optimizing a model, it gives insight into related variables that play the largest role in influencing the target metrics. This can add helpful context when making decisions about tempering / managing athlete training in-season to maximize peak performance for the right moments.

## Modeling

Since the target variables are all numeric, the planned approach to modeling involves regression analysis. We begin with a linear model approach, using Multiple Linear Regression in scikit-learn to further evaluate the strength of the features' linear relationships with the targets. Then, we'll use a Decision Tree approach to re-assess feature importance without adhering to strictly linear projections. The idea behind a multi-faceted modeling approach is that it offers different perspectives in testing predictor relationships to the response. 

I'll be evaluating the model performance with **Root Mean Squared Error (RMSE)** as it effectively describes the average distance of actual points from model predictions (error) and it is a popular choice to evaluate regression models (the better the model, the lower the RMSE). To make a final assessment on relevant variables, I'll be observing the selected features for **Feature Importance** as it is a metric in scikit-learn that evaluates how much a feature contributes to the final prediction (better predictors have higher feature importance). 

Fitting a linear model necessitates the data meets specific assumptions. The diagnostics for each model are viewable in the jupyter notebook, as I'll be reviewing the model results exclusively here. Also, to effectively evaluate the models, I'll be performing k-fold cross-validation and assessing the average RMSE of the folds. The random selection of examples in cross-validation ensures that the model predictions are generalizable and not just optimized to the current set of data.

We start with `Jump Height`.


![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/JumpHeight-LM.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/JumpHeight-LM-Features.png)

Linear model.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/JumpHeight-DT.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/JumpHeight-DT-Features.png)

Decision tree model.

I initially fitted a linear regression model with L1 regularization. This technique automatically scales the coefficients in the model to maximize the influence of relevant predictor variables. The model is predictably strong with an average RMSE of .43 (as the features are measures of the same movement), and `Peak Relative Propulsive Power` was the most relevant feature. When modeling for `Jump Height` with a decision tree, the model performed slightly worse than the linear model (.56 RMSE), and the strongest weighted feature was `Peak Velocity`, followed by measures of Propulsive Power.  

Modeling `RSI` next.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RSI-LM.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RSI-LM-Features.png)

Linear model.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RSI-DT.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RSI-DT-Features.png)

Decision tree model.

The regression model performed well (RMSE = .27), and the decision tree model performed similarly to the linear model (RMSE = .29), with the highest scoring feature being `Relative Force at Min Displacement`. 

When considering both models, measures of Force at Min Displacement are the strongest predictors for RSI.

Moving on to `Peak Force` in the Isometric Mid-Thigh Pull Test data.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/PeakForce-LM.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/PeakForce-LM-Features.png)

Linear model.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/PeakForce-DT.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/PeakForce-DT-Features.png)

Decision tree model.

The linear model performs extremely well due to many variations of `Peak Force` existing in the dataset (RMSE = .03), while the decision tree model is less effective (RMSE = 97). The top predictor of peak force is `Force at 200 ms` when assessing both models.

Repeating the process for the last target metric `Peak RFD`.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RFD-LM.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RFD-LM-Features.png)

Linear model.

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RFD-DT.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RFD-DT-Features.png)

Decision tree model.

The linear model with regularization (RMSE = 109) outperformed the decision tree model (RMSE = 221), but `Impulse 0-250ms` or `Net Impulse 0-250ms` was the most relevant feature across both models. In the next section, I'll be visualizing the trends of the relevant features alongside the original target metrics.

## Results

![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/JumpHeight-Variables.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RSI-Variables.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/PeakForce-Variables.png)
![alt text](https://github.com/mithilguru/Illinois-Strength-Trends/blob/main/Visuals/RFD-Variables.png)

Displayed above are the target metrics and influential factors of the Drop Jump and Isometric Mid-Thigh Pull tests visualized over testing period. As evidenced by the correlations, models, and trends over time, these are highly-related measures and are best used in conjunction to form a more complete picture of an athlete's training progress. A likely use-case would be considering these supplementary factors in addition to the standard target metrics when deciding on tapering athletes prior for meets / events.

## Discussion

As sports science continues to become an integral part of the overall training regimen for athletes worldwide, it's become increasingly important to understand the full extent of performance technology such as the Hawkin Force Plates system. With vast amounts of data at hand, accurately deciphering key metrics emerges as a pivotal task in strength coaching. 

Analyzing the Illinois Men's Gymnastics Drop Jump and Isometric Mid-Thigh Pull tests unveils the following insights: 
* For Drop Jumps, along with `Jump Height` and `RSI`, `Peak Relative Propulsive Force`, `Peak Velocity`, and `Relative Force at Min Displacement` offer vital context for assessing athlete performance
* In the Isometric Mid-Thigh Pull, `Force at 200 ms` and `Net Impulse 0-250ms` complement `Peak Force` and `RFD`.

A modeling limitation arises from the tightly interconnected variables collected by the force plates. This added challenge to understanding the relevance of individual measures, as models sought performance balance while retaining fundamental features (since the aim was feature evaluation). Modeling solely for precise target metric prediction (e.g., `Jump Height`, `RSI`, `Peak Force`, `Peak RFD`) requires a distinct approach focused on reducing the dimensionality of the dataset and collecting more data in frequent intervals to optimize model strength. Exploring this avenue would be an exciting approach for future analysis, particularly in evaluating training approaches for optimizing test performances.
