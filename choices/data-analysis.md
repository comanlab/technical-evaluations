# Focus: Data Analysis

This choice focuses on data analysis. After reading through the background and scenario below, please implement a solution to the prompt that follows.

The programming language we prefer you use is: **Python**. You may use any open sourced materials you'd like.

## Background

When we study real-world phenomena online, we rely heavily on datasets that are accessible via API. To observe and make sense of behaviors online, this may mean implementing various classes that connect to APIs and collect data (e.g., from social media, financial institutions, and government agencies). A lot of this data is textual in nature, and we analyze text with natural language processing methods that help us understand sentiment, parts of speech, etc. While many methods exist to analyze language, we tend to use only those methods that are backed up by psychological evidence. An example of these methods for sentiment classification of text is [VADER](https://github.com/cjhutto/vaderSentiment) (Valence Aware Dictionary and sEntiment Reasoner).

## Scenario

We want to analyze quotes from "The Office U.S." series. Luckily, a publicly accessible [API exists](https://akashrajpurohit.github.io/the-office-api/) for that. By collecting all the [listed quotes](https://github.com/AkashRajpurohit/the-office-api/blob/main/data/quotes.json), we have the opportunity to understand aspects of the language used throughout the series. We are particularly curious to learn how often each character expresses positive or negative emotions. Unfortunately, there are hundreds of quotes between the characters, and reading through and labeling them one-by-one isn’t an efficient or statistically rigorous method for understanding their emotional expressions. How do we make sense of use of emotion in quotes from The Office?

## Prompt

Suppose we want to analyze the emotional expression of all unique quotes from the public API for The Office. To collect that many quotes, we need to call the API more than once — there’s a response limit of one quote at a time at the exposed endpoint `/quote/:id`. Once we have every quote, we need to clean the text as preparation for sentiment analysis. 

**Your task is to implement a collection of methods that enable us to collect and classify sentiment in quotes by every member of The Office.** You should try to accomplish the following in your solution:

1. Handle API requests to collect all the quote data from the API, accounting for status codes and encodings of responses. Response errors should be handled gracefully and not stop your data collection process.
2. Store the collected API responses as a dataframe, where each response is a row.
3. Clean the quote text only to the extent recommended for the VADER model.
4. Apply VADER’s sentiment intensity analyzer to every quote and use the scores to label each text as either positive, neutral, or negative.
5. Return a chart that compares sentiment labels between characters' quotes in The Office.
6. Return a chart that compares the distribution of sentiment scores between characters' quotes.
7. _Challenge_: Compute the semantic similarity of quotes using [sentence-transformers](https://github.com/UKPLab/sentence-transformers) and the cosine similarity approach, then compare aggregate similarity scores bewteen Michael Scott and Dwight Schrute quotes.
