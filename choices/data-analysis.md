# Focus: Data Analysis

This choice focuses on data analysis. After reading through the background and scenario below, please implement a solution to the prompt that follows.

The programming language we prefer you use is: **Python**. You may use any open sourced materials you'd like.

## Background

When we study real-world phenomena online, we rely heavily on datasets that are accessible via API. To observe and make sense of behaviors online, this may mean implementing various classes that connect to APIs and collect data (e.g., from social media, financial institutions, and government agencies). A lot of this data is textual in nature, and we analyze text with natural language processing methods that help us understand sentiment, parts of speech, etc. While many methods exist to analyze language, we tend to use only those methods that are backed up by psychological evidence. An example of these methods for sentiment classification of text is [VADER](https://github.com/cjhutto/vaderSentiment) (Valence Aware Dictionary and sEntiment Reasoner).

## Scenario

We want to analyze [Ron Swanson](https://en.wikipedia.org/wiki/Ron_Swanson)’s quotes from the Parks & Recreation TV show. Luckily, a publicly accessible [API exists](https://github.com/jamesseanwright/ron-swanson-quotes?tab=readme-ov-file#ron-swanson-quotes-api) for that, which returns random quotes. By collecting his quotes, we have the opportunity to understand Ron Swanson’s language used throughout the series. We are particularly curious to learn how often Ron Swanson’s statements express positive or negative emotions—many viewers of the show seem to think he’s always in a bad mood. Unfortunately, he has a lot of quotes, and reading through and labeling them one-by-one isn’t an efficient or statistically rigorous method for understanding his emotional expressions. How do we make sense of Ron Swanson’s use of emotion in language?

## Prompt

Suppose we want to analyze the emotional expression of at least 250 unique Ron Swanson quotes from the public API. To collect that many quotes, we need to call the API more than once — there’s a response limit of ~108 quotes for any given call to the `/v2/quotes/<count>` endpoint. Once we have the required number of unique quotes, we need to clean the text as preparation for sentiment analysis, for which we will use VADER. 

**Your task is to implement a collection of methods that enable us to collect and classify sentiment in at least 250 unique Ron Swanson quotes.** You should try to do the following features in your solution:

1. Handle API requests, accounting for status codes and encodings of responses. Response errors should be handled gracefully and not stop your data collection process.
2. Compile 250 unique quotes into a single list. This API does track state for clients, so the same quote may be returned in many responses. (The same is true for many of the APIs we work with in our lab.)
3. Clean the text only to the extent recommended for the VADER model.
4. Apply VADER’s sentiment intensity analyzer to every quote, labeling each text as positive, neutral, or negative.
5. Return a bar chart comparing counts of each sentiment class.
