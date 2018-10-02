# Is Success on Kickstarter Pure Chance?
Analysis of Kickstarter Data - what makes a project successful?

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

### Data Analysis
Here I wanted to get a better idea of what the dataset looks like. I first looked at the distribution of countries,which shows that projects are predominantly from the U.S. (around 80%), followed by Great Britain (~10%) and Canada(<5%). Looking at the Kickstarter projects by category comes up with some surprising results. The most common category a project falls into is Film & Video (17%), then Music (14%), and Publishing (11%). What surprised me is that only about 9% of projects fall into the Technology category (good for 5th most common). It seems that Kickstarter is not a technology incubator but rather more artsy.

I continued the data analysis by producing more graphs of distributions or looking at interquartile ranges and percentile values.

#### Descriptive Statistics
I was hoping to see some real insight when looking at heatmaps of correlation matricies using Seaborn. This is a really handy tool that is great at visualizing correlations.

The only significant take aways is that Music, Theater, Dance and Comics were the categories most correlated with success.
Otherwise, the number of backers and dollars already pledged were a good sign of success, but that does not help with our aim of finding predictors.

### ML Classifier
Since the investigation of descriptive statistics wasn't getting me too far, I wanted to see what a supervised machine learning algorithm would use to predict success of a kickstarter project. I chose an ensemble method - Random Forest Classifier - because they have proven to be robust, easy to implement, and simple to get the feature importance. Since it is not a distance based classifier I decided not to scale and standardize the numerical features.

I removed `usd_pledged_real` and `backers` features as these were going to distort our model.

## Licensing, Authors, Acknowledgements, etc.
Data from: https://www.kaggle.com/kemical/kickstarter-projects
