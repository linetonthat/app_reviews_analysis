# Analysis of app reviews

Being interested in air quality awareness, I'm curious about what apps are available for this purpose, and what are the feedbacks from their users.
My main questions are:
* What apps are there?
* What are their main features?
* How do these apps work? Can we categorize them?
* How are they rated?
* What are users looking for when using those apps?
* What expectations are not currently met?


To try to answer these questions, I've collected some data: [features and reviews from selected apps on the app store](https://github.com/linetonthat/appstore_scraping/). 
In this project:
* Features and reviews are preprocessed using NLP tools as needed
* Several analyses are performed to better understand main app features and user expectations.

---
## So far
* Defined a strategy to analyse data
* Preprocessed text - In the reviews, abbreviations are used (eg NorCal for Northern California), some proper nouns are written in lowercase or are mispelled, emoticones and emojis are used. In order to allow for correct recognition and classification, some preprocessing is required.
   - [Open reviews file and convert to CSV_AirVisual_USA.ipynb](https://github.com/linetonthat/app_reviews_analysis/blob/master/preprocessing/Open%20reviews%20file%20and%20convert%20to%20CSV_AirVisual_USA.ipynb) Load and pre-process data (JSON format) to export dataset as CSV
   - [Removing_some_abbreviations.ipynb](https://github.com/linetonthat/app_reviews_analysis/blob/master/preprocessing/Removing_some_abbreviations.ipynb) - Identify main abbreviations and expand them in the review title and review text.
   - [Preprocessing_emoji_emoticons.ipynb](https://github.com/linetonthat/app_reviews_analysis/blob/master/preprocessing/Preprocessing_emoji_emoticons.ipynb) - Identify emojis and emoticons, and replace them with words in the review title and review text.
* Extracted opinion units
   - [Sentence segmentation](https://github.com/linetonthat/app_reviews_analysis/blob/master/NLP/Testing%20sentence%20segmentation.ipynb) Segment reviews in order to extract "opinion units": On top of default segmentation from spaCy, define a set of rules to refine sentence segmentation from reviews. For example, add a segmentation at "but" and "although". Decided to use the review title as an opinion unit as well.
* Analyzed
   - [Named_Entities_Recognition.ipynb](https://github.com/linetonthat/app_reviews_analysis/blob/master/NLP/Named_Entities_Recognition.ipynb) - Identify countries and regions where users would mostly use their air quality apps: Test Named Entity Recognition from spaCy with the following labels: 'GPE' (Countries, cities, states), 'LOC' (Non-GPE locations, mountain ranges, bodies of water) (and even 'NORP'(Nationalities or religious or political groups))

---
## On-going activities:
* Identify and quickly test methods to implement this strategy
* Learning how to perform preprocessing (NLP methods: spaCy, nltk, RAKE-nltk libraries)
* Identify classification tags
   - Identify topics and subtopics of interest
   - Extract keywords from opinion units
   - Assess semantic similarity of keyword vectors with subtopic vectors: Having to investigate what's the right threshold for semantic similarity (if it can be defined...)
   - Perform tagging opinion unit for a given topic in order to allow for an opinion unit to have several tags if needed
   - Investigate rule-based tagging to account for "Feature request"
* Label reviews according to sentiment (positive, neutral, negative)
   * Testing modules to assess sentiment scores based on words used (nltk's VADER), as it allows working on unlabelled data. 
* Defining and adjusting a pipeline for preprocessing reviews based on our first analyses


---
## Next steps:
* Test sentiment classifiers
* Tag reviews to have a training dataset
* Test topic classifiers
* Investigate "live" apps: Are apps still maintained? Downloaded?
* Have a look at the review texts (strange feeling when reading some of them)
   
