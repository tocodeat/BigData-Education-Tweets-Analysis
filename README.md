# Is Twitter a credible source of information that reflects emergence of important trends or topics in education?

The goal is to examine tweets related to education topics in 2022 and identify patterns and trends in education. To accomplish this, pySpark was used on Google Cloud clusters to analyze tweets related to K-12/Higher Education. This analysis answers the following questions:

1. Identify the most prolific / influential Twitterers
2. Who are these Twitterers (government entities / universities / schools / nonprofit organizations / news outlets / social media influencers / someone else)?
3. Visualize the distribution of tweet / retweet volume by Twitterers and types of organizations
4. Where are these Twitterers (all of them, not just influencers) located?
5. Is there any relationship between the emergence of new issues in education and progression and locations of these Twitterers?
6. Visualize the geographical distribution
7. What are the timelines of these tweets? Do you see significant peaks and valleys?
8. Do you see any data collection gaps?
9. Plot the timelines of these tweets
10. How unique are the messages?
11. Are they mostly unique? Or usually people are just copy-pasting the same text?
12. Visualize message duplication for each group of Twitterers (government entities / health organizations / news outlets / social media influencers / other)

## Data

The data is taken from the Twitter API spread across numerous .json files. It had a combined size of approximately 500 GB. This data comprises roughly 100 million tweets from users between April 2022 and February 2023. The data is organized into various columns of information pertaining to each tweet, including details about the user who posted it, the tweet's engagement metrics (likes, comments, retweets), the tweet's location, and other related entities (as described in https://dev.twitter.com/overview/api/tweets).

## Methodology

1. Discarded irrelevant tweets
2. Performed EDA to identify relevant variables for profiling Twitter users 
3. Identified the most prolific and influential Twitter users by message volume and retweets and categorized them based on their organizations 
4. Visualized the distribution and location of Twitter users, detected data collection gaps, and analyzed message uniqueness and duplication. 
5. Repeated the above steps for two specific topics, Critical Race Theory in the US and Hijab Row in India, to determine if there were any spikes in Twitter activity or shifts in geographical distribution of Twitter users related to these topics. 
6. Analysed similarities using functionalities such as MinHash and LSH using Jaccard distance metric.

The data was processed on Spark using Python and relevant libraries, including Pandas, Matplotlib, and NLTK.

## Tweet Clean-up and Filtering

1. Started with a 100M instances on Education
2. Filtered out non-English tweets, which improves the accuracy of the analysis for English-speaking regions. Later, two specific topics were analyzed which were trending in the USA and India, regions where a significant portion of tweets are made in English.
3. Used a list of 68 key words given by ChatGPT to filter tweets related to K-12 & Higher Education.
4. Removed tweets that contain violent or inappropriate language to avoid skew in the results. Used 54 keywords given by chatGPT.
5. Ended up with 40M instances.

For tweet similarity analysis, removed non alphanumeric words/text and lowered the case and removed stopWords from english dictionary

## Feature selection

Performed a quality check by computing the percentage of missing values in each column and dropped most of the columns with missing values greater than 70% 

## Conclusions

1. Twitter can be a valuable tool for tracking emerging trends and important topics in education, but caution should be taken in interpreting the results.
2. The high volume of tweets in September are most likely related to the beginning of a new academic year in many countries rather than any new topic in education.
3. News organizations are the most prolific Twitter users, while celebrities are the most influential Twitter users by retweet volume. This could lead to a biased representation of the topics. 
4. The top four countries with the highest number of Twitter users in education are the USA, Nigeria, India, and England, with the highest number of Twitter users in Asia.
5. The timeline of tweets in Asia shows a pattern unique to India, which is related to college admission exams and enrollment season.
6. Tweets about CRT and Hijab are concentrated in North America and India, respectively, and were influenced by recent events.
7. The analysis also shows that messages are mostly unique, but selecting different Jaccard similarity for different organizations and topics may result in a different result.

## Actionable recommendations

1. Provide tools (similar to google trends) for analyzing tweets: Twitter should provide tools for analyzing tweets to make it easier to identify trends and important topics. These tools should enable users to filter out irrelevant tweets and focus on relevant tweets. They should also enable users to identify influential Twitter users and categorize them based on their organizations.
2. Promote verified education-related accounts: Twitter should promote verified education-related accounts to increase their visibility and credibility. These accounts could include news organizations, universities, and education-related government agencies.
3. Provide a mechanism for flagging inappropriate content: Twitter should provide a mechanism for flagging inappropriate content. This will help ensure that are free from violent or inappropriate language.
4. Work with education organizations to increase engagement: Twitter should work with education organizations to increase engagement on the platform. This could include hosting Twitter chats on education-related topics or promoting education-related events on Twitter.
5. Highlight important topics in education: Twitter should highlight important topics in education to increase awareness and promote discussion. This could include promoting tweets related to important education-related events or featuring tweets from influential education-related Twitter users.




