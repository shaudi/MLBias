# Case Study - US Census Bureau: Bias in Surveys

## Overview

One of the most common machine learning use cases in government is that which relates to machine learning techniques for survey research. The Census Bureau, U.S. Bureau of Labor Statistics, and the U.S. Department of Agriculture (NASS) among other agencies have done practical work in this area [(Source)](https://arxiv.org/pdf/1812.10422.pdf). This case outlines how the US Census is identifying and mitigating bias in its Commodity Flows Survey.

## How is machine learning used by survey methodologists?

Machine learning methods are of great value to survey methodologists. First, ML methods are algorithmic and use data to describe the data generating mechanism. There is an important distinction between models created and used for explanation versus prediction. Of these two types, traditional methods involve explanatory models, while the other uses predictive models to forecast continuous outcomes, or classify categorical outcomes, with the latter being the most common variation. While machine learning or algorithmic methods can be used to refine explanatory models, their most common application lies in the development of prediction or classification models. In survey settings, there is often overlap between these two classes of models [(Source)](https://www.nber.org/system/files/chapters/c14278/c14278.pdf).

Predictive models are constructed from data and use associations between predictor variables and the target outcome, minimizing estimation variance and bias and in this process trading off some accuracy for improved empirical precision. In contrast to many explanatory models, the predictive model functional form is often not given in advance, often lacking a table of coefficient estimates or specific statistics that evaluate the significance of a given predictor variable using ex ante variables.

As it relates to survey research, in the case of responsive designs, where the goal is to predict nonresponse, the types of these variables can include those variables known for all sampling units or paradata that are collected on all sampled units. While obviously related to survey response, they may not provide a full accounting of why sampled persons or households participate in the survey or answer a given item. The critical difference is that in this scenario, we are less interested in fully explaining or confirming the causal mechanisms of nonresponse and more concerned with correctly classifying sampled units as respondents or nonrespondents, and using this classification as the basis of tailoring or adjustment.

Most of the machine learning methods used by survey metholodigsts are to predict a binary survey response variable -- for example, variables corresponding to categories of age, sex, education, race, income level that are coded as yes/no -- of a respondent. Clearly, when predicting response variables tied to data that can directly influence sensitive and human-recognizable populations like race or gender, which could be used to influence policies affecting these populations, preventing the bias takes on increased importance.

## How is machine learning applied to survey work in the Census Bureau today?

*Application Focus: Autocoding*

We examine the case of “autocoding.”  Briefly, coding is a task that classifies an object to a corresponding code, and is useful for large surveys, which contain large numbers of objects and codes/classes and wherein results must be released to the public on a tightly-controlled schedule.  For automatically mapping survey responses, autocoding can be leveraged to improve data processing, improve efficiency several-fold, and reduce labor hours. 

To implement autocoding,  there are two distinct types of methodologies. One is supervised classification methods (including machine learning techniques) and the other is rule-based methods. We focus on the machine learning methodology.

One active and illustrative federal government example of using this approach is that of Census Bureau researchers, who have described the use of North American Industry Classification System (NAICS) Economic Census Write-in Autocoder in their work 
[(Source)](https://www.census.gov/content/dam/Census/newsroom/press-kits/2017/jsm/jsm-presentation-dumbacher-hanna.pdf).  In short, they use ML to assign a NAICS code to an SDKB written survey response from the Economic Census, an important national survey conducted by the Census Bureau every five years to collect comprehensive statistics about business activities and businesses throughout the entire United States.  Their approach was to train a model based on 3 years worth of Economic Census data consisting of 1.5 million responses. They purged nonresponses, invalid responses (“n/a”), removed stop words, punctuation, and whitespace, and created features using word sequences occurring throughout the document.

The information from this coding output comes from the Economic Census, the IRS, the Social Security Administration.  Advantages of using an autocoding approach including overcoming the expense,  time-consuming manual approach to coding (again, recall that federal government survey processing deadlines are fixed and  inflexible), and the risk of introducing certain types of systematic errors.

<img width="648" alt="image" src="https://user-images.githubusercontent.com/80533280/114552284-6f079d80-9c32-11eb-85b3-2ec8afdcc49c.png">


<img width="647" alt="image" src="https://user-images.githubusercontent.com/80533280/114552359-847cc780-9c32-11eb-8693-b50ef2d23bd5.png">



## How does machine learning bias affect real-life official statistics work in government?

The Commodity Flow Survey (CFS) is a joint effort between the Bureau of Transportation Statistics within the U.S. Department of Transportation (DOT) and the U.S. Census Bureau. The survey program produces estimates of the volume of domestic movement of goods by origin geography, destination geography, the product shipped, and mode of transportation. Policymakers at the national and local levels use CFS estimates to make infrastructure planning decisions. 

An example of how CFS data are used for decision-making is shown in the below figure. U.S. DOT’s Bureau of Transportation Statistics and Federal Highway Administration take CFS estimates and combine them with other data sources to produce a comprehensive picture of domestic freight activity. This data product – the Freight Analysis Framework – also helps forecast freight demand on the U.S. highway network for the future, as seen in the figure below. Data like these then help inform policymakers’ infrastructure funding decisions for the highway network. Given the use of CFS data for making these decisions, it is important to minimize any sources of bias that may adversely impact resource allocation.


<img width="654" alt="image" src="https://user-images.githubusercontent.com/80533280/114552796-f6551100-9c32-11eb-9c2a-f8b6a5584a65.png">



Bias is not a new issue for the CFS – as with all other Census Bureau surveys, the CFS routinely conducts studies of non-response bias. However, the CFS program recently introduced a new innovation: using Machine Learning (ML) to autocode product descriptions provided by survey respondents. Previously, the survey asked respondents – in the case of CFS, businesses across the country – to look through a book of 514 product codes to find the one that best fit the product they were shipping. This innovation has substantially improved data quality and reduced burden on those businesses, but implementing this new method required a close examination of potential sources of bias to mitigate undesired negative outcomes.

When investigating bias in ML, it is key to have a deep understanding of every stage of the data generation and modelling process – from when the input data for machine learning are initially created, to the outcomes, predictions, and allocations of the model itself. Here are a few potential sources of bias in our ML pipeline and our solutions to address these issues.

## Potential biaseses and solutions

- **Response bias**: The initial ML model used respondent-provided descriptions and product codes as its training set. Due to the burdensome nature of the product code lookup process and limitations in the product code search tool that Census offered, we found that respondents would systematically misclassify product codes they provided. Because the model is trained on respondent-provided data, this means it will inherit the same biases and misclassifications that respondents make. 

- **Omitted variable bias**: Limitations in the CFS form meant that respondents were only able to provide 150 characters of product description. This meant that respondents who provided more detail had their descriptions truncated. Potentially, this could mean that our model is missing key contextual information – again leading to systematic misclassifications.

- **Solution for response and omitted variable bias**: Evaluate impact of ML on data products. Ultimately, the CFS program publishes estimates of the volume of different products moving across the country. We can evaluate how shares of different product types have changed as the result of using ML. In doing so, we can ensure that our model has not inherited any of the biases introduced by respondent misclassification, technical issues with the form, or even other issues we may not have foreseen. By tracking changes in estimates over time, we can monitor and diagnose the cause of changes in product shares and ensure they are not the result of a biased ML process. The below figure illustrates one way that we track these impacts on our product category shares.

- **Automation + confirmation bias**: To ensure the model is assigning high-quality product codes, we have subject-matter experts validate the model’s predictions. Analysts may be predisposed to confirm the model’s classification, leading to confirmation of incorrect product codes and reinforcement of the model’s biases.

- **System drift**: As we implement this ML in production, we have to keep in mind that products themselves change over time and new products are introduced into the marketplace. Does our coding scheme capture this, and can our ML model appropriately classify those new or changed products? 

- **Solution for automation/confirmation bias and system drift**: continuous evaluation of a gold standard. Rather than have analysts confirm the model’s predictions, our subject matter experts developed a “gold standard” of products and their associated product code, without looking at any of the model’s outputs. We evaluate the model’s performance on this gold standard to ensure it is making high quality predictions. In addition, by continuously updating this gold standard and re-evaluating over time, we make sure to avoid issues with changes in products over time.

We see that after applying these techniques, there was a significant decrease in miscellaneous products, which was a desired outcome because ML could more appropriately code many records that respondents had labelled as “miscellaneous”


<img width="658" alt="image" src="https://user-images.githubusercontent.com/80533280/114552666-d7567f00-9c32-11eb-92f5-72d52698aa8d.png">


To conclude, practitioners need to be aware of both the context around the potential impacts of introducing ML into a production process, as well as have a deep understanding of all of the steps that lead to the development of an ML model. An understanding of all aspects of training data and the limitations of that data is especially key, but as we have discussed, bias can be introduced at many points in the process. While we can never completely eliminate bias from our statistical estimates, practitioners should evaluate the impacts of ML-based processes and regularly work with subject-matter experts to validate model outputs and ensure that ML models are correctly calibrated.


### References

Cuffe, J., Bhattacharjee, S., Etudo, U., Smith, J. C., Basdeo, N., Burbank, N., & Roberts, S. R. (2019). Using Public Data to Generate Industrial Classification Codes. In Big Data for 21st Century Economic Statistics. University of Chicago Press.

Federal Highways Administration. (2019). “Average Daily Long-Haul Freight Traffic on the National Highway System: 2045 Map.” (last accessed 6 April 2021, last updated October 9, 2019). 
https://ops.fhwa.dot.gov/freight/freight_analysis/nat_freight_stats/nhsavglhft2045.htm

Moscardi, C. (2020). “Bias in Commodity Flow Survey ML: A Case Study.” Presented to 18F Ethics Working Group 02-2020. https://github.com/census-bds/cfs-ml-bias/blob/main/ML%20bias%20in%20the%20Commodity%20Flow%20Survey.pdf 

Strobl, C., Malley, J., & Tutz, G. (2009). An introduction to recursive partitioning: rationale, application, and characteristics of classification and regression trees, bagging, and random forests. Psychological methods, 14(4), 323–348. https://doi.org/10.1037/a0016973

Toth, D., Phipps, P. (2014). Regression tree models for analyzing survey response. Proceedings of the Government Statistics Section, American Statistical Association, 339–351, https://www.bls.gov/osmr/pdf/st140160.pdf (last accessed 10 December 2018).



**To Note: CFS Bias Use Case
The Census Bureau has reviewed this data product for unauthorized disclosure of confidential information and has approved the disclosure avoidance practices applied.  (Approval ID:  CBDRB-FY20-ESMD002-010).
 
Disclaimer: Any opinions and conclusions expressed herein are those of the author(s) and do not represent the views of the U.S. Census Bureau or the U.S. Department of Transportation. All results have been reviewed to ensure that no confidential information is disclosed.**





