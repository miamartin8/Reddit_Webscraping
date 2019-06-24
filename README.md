# Reddit Webscraping and Natural Language Processing: *r/Relationships and r/BreakUps*

# Problem Statement

Can reddit posts from r/Relationship and r/BreakUps subreddit threads be classified into their respective thread based on their title?

# Gather Data

I scraped from multiple subreddit pairs, and ended up chosing r/relationships and r/BreakUps.  I started with r/recipes and r/zero 
waste recipes.  I found these subreddits posed an issue because most of the posts were either videos, images or links to 
websites.  There was not enough text to analyze in these threads.  I then chose r/LearnPython and r/ProgrammerHumor.  
This also posed an issue because while r/LearnPython had a lot of text, r/ProgrammerHumor was a lot of images.  I settled 
on r/relationships and r/BreakUps because both of these have a lot of text (they're stories), they are about similar subjects, 
but I expect there will be some differences to differentiate the threads.  Perhaps more negative content in break ups and more 
positive content in relationships.

I originally scraped 500 posts from each thread.  When I finished my model, I found there was a large gap between the train and test 
score.  I increased the scrape to approx. 1000 posts per thread.  This improved the score variance between the trian and test.

# Explore the Data

In exploring the scraped data, I discovered that there were a lot of posts where the text was removed.  However, all the posts in both 
threads had very descriptive titles.  I decided to create my model using the titles from these threads.  The format of the titles seemed 
to vary between the two threads, so I thought this would increase the predictive ability of the model.

# Model with Data

### Type of Vectorizer
 
1. Hashing Vectorizer
2. Count Vectorizer

### Type of Model

1. Naive Bayes Bernouli Model
2. Logistic Regression
3. Ridge Regression


# Evaluate Model

The **hashing vectorizer** with a **Bernouli Naive Bayes model** performed the worst on the train data with 52% accuracy 
score on training data.  The hashing vectorizer has the benefit of being fast, but it is less precise.  

The **count vectorizer** with a **Bernouli Naive Bayes model** performed much better with 94% on train data and 91% on 
test data.  

The **count vectorizer** with a **Logistic Regression model** performed the best with 97% accuracy on training data and 92% 
on test data.  The logistic model with a count vectorizer performed the best because:

1. The count vectorizer is more precise than the hashing vectorizer.
2. The logistic model was better fit to this classification problem than the Naive Bayes model.

# Answer Problem

Title can be used to predict classification of subreddit thread between r/Relationships and r/BreakUps with 92% accuracy, as shown 
in the logistic regression above using a count vectorizer.  

The formatting of the titles has a large impact on the predictive ability of the model.  Both threads discuss both relationships and 
break ups.  However, the r/BreakUps thread uses age and sex as identifiers in the title.  The r/Relationships thread includes more 
descriptive language in the title.

If I had more time and more data I would like to dive deeper into the predictive features in subreddit threads.  I think adding in the 
text of the thread would be a great feature to explore because it allows for more data (text is longer than title, therefore 
more content).  The data I scraped had too many posts with text removed, so I could not use text in this model.  I plan to scrape 
the data again at a later point to see if I can find more data without removed text.  
