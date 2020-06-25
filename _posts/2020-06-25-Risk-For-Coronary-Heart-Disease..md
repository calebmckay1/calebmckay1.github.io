# Predicting Risk For Developing Coronary Heart Disease

&ensp; &ensp; I recieved this dataset from Kaggle which has a shape of over 
4,000 rows and 16 columns, to predict a boolean target of whether a patient is at risk for developing coronary heart disease based on the values within those columns.

&ensp; &ensp; At first I viewed the majority class to see how accuracte we would be if we simply guessed the outcome based on our sample. Turns out it was
skewed. This means if we were to guess if a patient is at risk for developing
heart disease, we could assume "no", and be correct almost 85% of the time.


&ensp;

<img src='https://raw.githubusercontent.com/calebmckay1/calebmckay1.github.io/master/resources/Screenshot%202020-06-25%20at%201.19.55%20PM.png' width='500'>

&ensp; &ensp; I then went ahead and created x using the columns that didnt 
include our target data, and the y which did. Afterwards I used Smote to even out the classes. This is what happened.

&ensp;

<img src='https://raw.githubusercontent.com/calebmckay1/calebmckay1.github.io/master/resources/Screenshot%202020-06-25%20at%201.20.37%20PM.png' width='500'>

&ensp;


<img src='https://raw.githubusercontent.com/calebmckay1/calebmckay1.github.io/master/resources/Screenshot%202020-06-25%20at%201.21.04%20PM.png' width='500'>

&ensp;&ensp; Now that the target data (what we're predicting) is leveled out to roughly 50/50, it was time to train a model. At this point I ended up starting small and used a Logistic Regression model. Here's are the results:

&ensp;

<img src='https://raw.githubusercontent.com/calebmckay1/calebmckay1.github.io/master/resources/Screenshot%202020-06-25%20at%201.22.04%20PM.png' width='700'>

&ensp;&ensp; Yeah not the greatest.. This model beat the majority class of 50% for the train data but we could do better so I went ahead and created a different model using XGBClassifier.

&ensp;


<img src='https://raw.githubusercontent.com/calebmckay1/calebmckay1.github.io/master/resources/Screenshot%202020-06-25%20at%202.37.22%20PM.png' width='700'>

&ensp;&ensp; This ended up having a better accuracy score on all 3 subsets than the previous models, but I was curious how the features interacted with eachother, and which features had the most importance, so I created a feature importance plot using pdp, and this is which features had the most weight:

&ensp;


<img src='https://raw.githubusercontent.com/calebmckay1/calebmckay1.github.io/master/resources/Screenshot%202020-06-25%20at%202.43.41%20PM.png' width='350'>


&ensp;&ensp; From what the model shows, it appears as if the older you get the more at risk you become, which makes a lot of sense. Out of these features I wanted to view the interaction between 2 of them. I chose the top feature, age, and systolic blood pressure, and used feature interaction pdp to plot.

&ensp;


<img src='https://raw.githubusercontent.com/calebmckay1/calebmckay1.github.io/master/resources/Screenshot%202020-06-25%20at%201.25.02%20PM.png' width='500'>


&ensp;&ensp; Interpreting the plot you will see that the interaction between age and systolic blood pressure is clear. As you age, your systolic blood pressure will change, which again makes sense. The older you get the weaker your cells are becoming through time, and the most at risk you are for heart disease. Age is almost like a first order consequence, where with age there are more consequences that follow that are health related, such as more probable to break a bone due to fragile bones, more at risk for mentally for dimentia and alzheimer's, etc.

&ensp;&ensp; In conclusion it appears that the most important factor in determining if you are at risk for heart disease is age. The majority of people don't have it and the majority class in our sample concurs with this. It seems that making sure your blood pressure and BMI are in check are the small things that can go a long way in preventing this disease. 

&ensp;&ensp; I've created a web app to see if you're at risk, you can visit this app here:


