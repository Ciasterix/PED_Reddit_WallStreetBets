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
In this stage we created features from the images. Unfortunately some of them have been removed and replaced with placeholder. Images from i.redd.it were downloaded using the Reddit API. For images from outside Reddit, we used this library: https://github.com/mikf/gallery-dl

After a brief analysis of what is actually in the images, we created the following features:
- Placeholders (binary feature) whether a post had an image but it was removed and replaced with a placeholder 
- Mean, median, standar deviation and quantiles values in grayscale and for each of the RGB channels and SV channels from HSV color representation
- BagOfVisualWords - created by clustering the feature vectors obtained from the SIFT descriptor
- Using pretrained Neural Networks to extract features - https://tfhub.dev/google/imagenet/mobilenet_v1_025_128/feature_vector/5
- Features created on text extracted from images using pytesseract

## Phase 3: Feature Selection
In this stage, we tried to limit the number of features. We considered rejection of features:
- with too small variance,
- too weakly correlated with the target variable,
- by recursive feature elimination.

In the end we used only the second method, because the first one rejected features we considered important, while the last one required training of a good model, which we did not manage yet at this stage.
The number of features was reduced from **346 to 237**
