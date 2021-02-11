# Customer Churn Project
Determining Feature Importances with Telecom Customer Churn Data

<b>Jeff Spagnola</b><br><br>
jeff.spags@gmail.com<br>
<a href="jeffspagnola.com">Portfolio Site</a><br>
<a href="github.com/spags093">Githube</a><br>
<a href="linkedin.com/in/jeffspagnola">LinkedIn</a>

### Note:
<center><b> This Read Me is a work in progress and will be completed soon. </b></center>

## Introduction

<center><img src="2-8_telecom-media_v2_1600.jpg" alt="telecom image"></center>

Customer churn is a major concern for any business.  In today's world, the customer is more informed than ever and can find various offers and promotions for services with just a few taps on a mobile device.  With targeted social media ads, they may not even have to do that!  This fact alone makes it harder than ever to create a long-term customer when any misstep in customer management can send a loyal client jumping ship for a better offer somewhere else.  With so much competition in the telecom market, it's no surprise that many companies have issues with losing customers to competing companies.  Often, it is not 100% clear why these customers drop their current provider to leave for another.  

In this project, we will use data analysis and machine learning to figure out what factors most influence a customer's decision to leave their service provider for a competitor.  

## Obtain
The data comes from the Churn In Telecom dataset from Kaggle. There isn't much more info on Kaggle than is represented in the dataset, but if you'd like to check it out, <a href="https://www.kaggle.com/becksddf/churn-in-telecoms-dataset">click here</a>.

``` python
df = pd.read_csv('bigml_59c28831336c6604c800002a.csv')
print(df.shape)
df.head()

```
## Scrub
After briefly exploring the data, there's a few red flags in the info, specifically:
- Phone number being an object, although do we even need the phone number column for prediction?
- One hot encoding the states may lead to too sparse of a dataset
- Area code should be come categorical as opposed to a numerical value
- Our target, churn, being a bool as opposed to a (1,0)

### Phone Number
We can actually remove the phone number as it really has no bearing on the outcome of the project.
```python
df.drop('phone number', axis = 1, inplace = True)
```

### Area Code
After checking out the values of the area code, we came to find that it's only 3 area codes that are all located in the bay area.  This doesn't make too much sense as the State column shows that there are customers in each of the 50 states, plus Washington DC.  There's no documentation with the dataset to explain this, so we'll drop this column for now until an explanation can be found.
```python
df.drop('area code', axis = 1, inplace = True)
```


## Explore


## Modeling


## Interpret


## Conclusion
With so much competition in the telecom market, it's no surprise that many companies have issues with losing customers to competing companies.  Often, it is not 100% clear why these customers drop their current provider to leave for another.  

In this project, we have used data analysis and machine learning to figure out what factors most influence a customer's decision to leave their service provider for a competitor.  

### Results
<b> Throughout the course of this project, we have determined the following features are the most important contributing features to customer churn:</b>
- Total Day Minutes - The total amount of minutes spent on the phone during the day is the most important feature in terms of customer churn, though it affects the rate of churn both positively and negatively fairly evenly.  
- Customer Service Calls - The amount of customer service calls very negatively affects whether or not a customer leaves the company. 
- Total Evening Minutes - Similarly to total day minutes, total evening minutes has proven to be a very important feature but affects churn both positively and negatively to a similar degree. 
- No International Plan - Not having an international plan has a positive effect on keeping a customer. 
- Total International Calls - A caller who makes more international calls is more likely to stick with the company.

### Recommendations
<b> Based on these findings, we can make the following recommendations: </b>
- <b>Improve Customer Service </b>- Customers who make more calls to customer service tend to leave the company.  Based on this, we can infer that they experienced below average customer service experiences.  By improving the customer service protocols, we can prevent many customers from leaving. 
- <b>Don't Push an International Plan</b> - Customers who don't already have an international plan tend to churn less frequently than customers who have the international plan.  If we limit the offer of international plans to only the customers who require it, we can lower the rate of customer churn.
- <b> If a Customer Has the International Plan, Make Sure They Use It</b> - Customers who make more international calls tend to continue their service.  By making sure customers who do actually have international plans feel they are getting the full value of their plan, make sure they use the international calling options.

### Future Work
<b>With more time, we can enhance this project in the following ways:</b><br>
- <b>More Data:</b>  With more data, we can make the models more accurate and can perhaps pull different insights
- <b>Feature Engineering:</b>  We can experiment with some feature engineering and see if we can gain new insights into what features contribute to customer churn.
- <b>Modeling:</b>  We can spend more time fine tuning the models to make them more accurate. 