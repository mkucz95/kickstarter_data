# Crowdfunding Success  -  Chance or Strategy?
Analysis of Kickstarter Data - what makes a project successful?
[Click to View Project](http://htmlpreview.github.io/?https://github.com/mkucz95/kickstarter_data/blob/master/kickstarter_data.html)

## Installations
- Python: v.3.6.3
- Libraries Used: Sci-Kit Learn, Pandas, Numpy
- Kaggle API

## Project Motivation
I wanted to investigate to see whether there are any trends that contribute to project success. Having a successful round of crowdfunding can make or break a career or dream. I want to try and find something that would help people get on the right track to raising money.

## File Descriptions
- Jupyter Notebook File: kickstarter_data.ipynb
- HTML File of Notebook:
- Data Files: `ks-projects201612.csv`, `ks-projects201801.csv`

## Process

### Data Cleaning
There were two datasets that upon evalution turned out to be similar, except one also included data until 2018. I made sure of this by converting the project deadline dates into an identical format, sorted by the dates, which showed that there was significant overlap. Therefore I focused only on the 2018 dataset.

##### Data Engineering
I engineered a few variables to help with the analysis.
- `success`: I defined this by any project that had raised at least as much as its goal.
- `duration`: number of hours between launch and deadline
- `average_backing`: is pledged funding divided by the number of backers. It gives an idea of how excited some people could be, but also about the incentives presented in the project.

### Data Analysis
Here I wanted to get a better idea of what the dataset looks like. I first looked at the distribution of countries,which shows that projects are predominantly from the U.S. (around 80%), followed by Great Britain (~10%) and Canada(<5%). Looking at the Kickstarter projects by category comes up with some surprising results. The most common category a project falls into is Film & Video (17%), then Music (14%), and Publishing (11%). What surprised me is that only about 9% of projects fall into the Technology category (good for 5th most common). It seems that Kickstarter is not a technology incubator but rather more artsy.

I continued the data analysis by producing more graphs of distributions or looking at interquartile ranges and percentile values after I had split the data up into successful and unsuccessful projects. This would help me look at the difference between the two.

#### Descriptive Statistics
I was hoping to see some real insight when looking at heatmaps of correlation matricies using Seaborn. This is a really handy tool that is great at visualizing correlations.

The only significant take aways is that Music, Theater, Dance and Comics were the categories most correlated with success.
Otherwise, the number of backers and dollars already pledged were a good sign of success, but that does not help with our aim of finding predictors.

### ML Classifier
Since the investigation of descriptive statistics wasn't getting me too far, I wanted to see what a supervised machine learning algorithm would use to predict success of a kickstarter project. I chose an ensemble method - Random Forest Classifier - because they have proven to be robust, easy to implement, and simple to get the feature importance. Furthermore, it mimics a decision making process someone who wants to start a Kickstarter project could go through. Since it is not a distance based classifier I decided not to scale and standardize the numerical features. After using a out of the box Random Forest Classifier (from Sci-Kit Learn), I wanted to see how good we could I could get it. I utilized GridSearch to go through some of the parameters that I thought would make the biggest difference: `n_estimators`, `max_depth`, `min_samples_split`. These parameters define how many decision trees our ensemble learner will utilize, the highest number of layers a tree can have, and how many data points we need down a certain node to split that one into two children respectively. The accuracy of this optimized Random Forest Classifier did not improve significantly - 0.64 to 0.68 accuracy score. This is quite unsatisfactory and shows that it is rather quite difficult to predict.

I removed `usd_pledged_real` and `backers` features for training as these were going to distort our model, and we would not have them ex ante.

## Conclusion
I was able to answer three of the questions I had set out to answer. 
1. The biggest factor in having a successful kickstarter project is the funding goal you set yourself. The median successful project had a funding goal nearly half of the median unsuccessful project.
2. The most successful categories are Music, Film & Video, Dance, Comics - many of the arts.
3. There were quite a few differences between successful and unsuccessful projects. Other than the ones mentioned above, the median fundraising duration of a successful project was 7 hours shorter than that of unsuccessful projects. Maybe there is a sense of urgency that convinces people to donate. Furthermore, median pledge in USD is about 65$ for successful projects and only $17 for unsuccessful ones, which shows that one would be wise to incentivize higher values of pledges.

## Licensing, Authors, Acknowledgements, etc.
Data from: https://www.kaggle.com/kemical/kickstarter-projects
