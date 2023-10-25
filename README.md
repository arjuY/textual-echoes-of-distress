# Textual Echoes of Distress: Uncovering and Analysing Suicidal Discourse on Mental Health Subreddits
In this project, we focus on analyzing personal narratives related to mental health gathered from Reddit by harnessing the power of data science techniques. By employing suicide detection model, sentiment analysis and N-gram language modeling, this research allows us to explore the factors associated with mental illness and suicide in an online context, offering valuable perspectives that may inform future interventions and support strategies.

Ee focus on posts of last seven years i.e., from year 2016 to year 2022, that are related to four disorders, namely Anxiety Disorder, Depressive Disorder, Bipolar Disorder and Schizophrenia. Anxiety and Depressive disorders are the most common mental illness found around the world. With 301 million people living with an anxiety disorder in 2019 and 280 million people were living with depression, 40 million with bipolar disorder while Schizophrenia affects approximately 24 million people or 1 in 300 people worldwide, these disturbing numbers raise the concern of how many of these people might be contemplating suicide.

Using our trained NLP model, we label the posts as suicidal and nonsuicidal. Through this labelled data, we answer the following research questions:
1) Do the longer narratives of mental illnesses contain more suicidal content as compared to smaller ones?
2) Are individuals discussing about certain disorders tend to write more suicidal content?

# Dataset

1) Reddit_dataset: This analysis centres on posts spanning the past seven years, encompassing the period from 2016 to 2022. The data is collected using Pushshift Reddit API. It is RESTful API that provide the ability to search ‘submissions’ i.e., posts, on reddit by using the search submissions method. The resulting dataset, reddit dataset, has 365,419 rows of data from subreddits: anxiety (43.11%), depression (34.03%), bipolar (9.64%), schizophrenia (3.13%), mentalillness(10.08%).
2) Suicide_dataset: This is the subset of publicly available suicide dataset on hugging face. The rows labelled as ’suicidal’ in this dataset contain reddit posts from the popular subreddit ’SuicideWatch’ which has 434k members. The data was sampled and re-labelled to create the final suicide detection dataset which is used to train our suicidal content detection model. It has of 300 rows of labelled data for training with the total of 129 rows are labelled as ’suicidal’ and 171 are labelled as ’non-suicidal’.

#

