# Prediction Churn from telecom data

For this project I'm going to suggest a model to predict customer Churn for telecom companies. The data I used is available on [Kaggle!](https://www.kaggle.com/radmirzosimov/telecom-users-dataset)

## Description:

* customerID - customer id
* gender - client gender (male / female)
* SeniorCitizen - is the client retired (1, 0)
* Partner - is the client married (Yes, No)
* tenure - how many months a person has been a client of the company
* PhoneService - is the telephone service connected (Yes, No)
* MultipleLines - are multiple phone lines connected (Yes, No, No phone service)
* InternetService - client's Internet service provider (DSL, Fiber optic, No)
* OnlineSecurity - is the online security service connected (Yes, No, No internet service)*
* OnlineBackup - is the online backup service activated (Yes, No, No internet service)
* DeviceProtection - does the client have equipment insurance (Yes, No, No internet service)
* TechSupport - is the technical support service connected (Yes, No, No internet service)
* StreamingTV - is the streaming TV service connected (Yes, No, No internet service)
* StreamingMovies - is the streaming cinema service activated (Yes, No, No internet service)
* Contract - type of customer contract (Month-to-month, One year, Two year)
* PaperlessBilling - whether the client uses paperless billing (Yes, No)
* PaymentMethod - payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
* MonthlyCharges - current monthly payment
* TotalCharges - the total amount that the client paid for the services for the entire time
* Churn - whether there was a churn (Yes or No)


### Exploring the Data set

I start be cleaning up the data a little bit. I noticed that there was no correlation between the first column "Unknown: 0" and the Churn value and that the customer ID wouldn't be necessary for predicting Churn. Also, upon reviewing the df.info() output I realized that the "TotalCharges" columm would need to be converted to a numeric value. Besides that the data was very Clean to start off. 

after reviewing the set, I also decied to convert everything into dummy variables right away since it would be a bit easier to work with later on. The conversion dictionary is laid out the the legend.txt document for review. 


### Interesting Correlations 

To get a better understanding of the data I created a couple of correlation matrices for the features I thought would be the most significant in determining CHURN. 

I also just wanted to see if there were any notable differences between genders (the're weren't any). and I was interested to see how being a senior citizen would correlate with some of the features related to self-service. Interestingly, I didn't see that much of a correlation between senior status and paper-billing, automatic payments, and technical support. 


## Choosing the model

Given the fact that this data set consists mostly of categorical data, I decided to go with the simplest option to start: logistic regression. 
the results were surprizingly accurate at around 80% given the fact that I didn't run many tests to optimize the parameter tuning. Unfortunatly though the false negative rate was a little too high for this type of situation in my opinion. Since it is typically far more costly for telecom companies to attain new customers than it is for them to retain current customers. So I thought that I would try a different model with the aim of reducing this metric. 

The next model I tried was a Support Vector Machine. I was glad to see that the false negative rate was significantly lower with this model since that was my intention. However, the accuracy of the SVC model was about 10% lower than the logistic regression, so there is an interesting tradeoff there. 

In order to decide which model would be optimal between these too (or other, better optimized models) it would be important to take the cost of type one and type two errors into more serious consideration. 

### Summary

Overall, the Logistic regression provided the most accurate classification results at around %80. However, if we we're going to apply a model like this to target specific customer's for discounts and offers we would need to take the false negative rate into serious consideration by determining the approximate cost of losing a customer against the cost of the retention offer required to prevent churn. whith that information we'd be able to optimize this model to it's full cost saving potential. 
'
