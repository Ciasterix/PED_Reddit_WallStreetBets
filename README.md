# PED_Reddit_WallStreetBets
Project for our Data Mining course (pol. *Projekt Eksploracji Danych - PED*) at Poznan University of Technology, co-created with Krigaree.

## Project goal
The goal of the project is to model and predict the popularity of posts, that is, the values of the score and comms_num columns, based on the characteristics of the posts

## Dataset
https://www.kaggle.com/gpreda/reddit-wallstreetsbets-posts
The collection had outdated values for the score and number of comments. We updated them using the Reddit API

# Project phases

## Phase 1: Analysis of the dataset and Text Attributes
In this step, we performed an analysis of the attributes (columns in the table), their meanings, distributions and statistics. We have checked, among other things, what are the most frequent words in titles and bodies and what type of links or resources were most frequently attached to posts. After the analysis, we conducted feature engineering.

The texts in titles and bodies were preprocessed by:
- removing punctuation and stopwords
- replacing emoticons with special tokens
- lemmatisation,
- converting all letters to lowercase

After the analysis, we carried out feature engineering by creating various attributes such as title and body length, type and number of emoticons, sentiment, LDA topic, and publication time as a number of minutes/hours/days since the beginning of the analysed period. A total of 50 different features were created.

## Phase 2: Image Attributes
