# Textual Echoes of Distress: Uncovering and Analysing Suicidal Discourse on Mental Health Subreddits
In this project, we focus on analyzing personal narratives related to mental health gathered from Reddit by harnessing the power of data science techniques. By employing suicide detection model, sentiment analysis and N-gram language modeling, this research allows us to explore the factors associated with mental illness and suicide in an online context, offering valuable perspectives that may inform future interventions and support strategies.

This project focuses on posts of last seven years i.e., from year 2016 to year 2022, that are related to four disorders, namely Anxiety Disorder, Depressive Disorder, Bipolar Disorder and Schizophrenia. Anxiety and Depressive disorders are the most common mental illness found around the world. With 301 million people living with an anxiety disorder in 2019 and 280 million people were living with depression, 40 million with bipolar disorder while Schizophrenia affects approximately 24 million people or 1 in 300 people worldwide, these disturbing numbers raise the concern of how many of these people might be contemplating suicide.

Using our trained NLP model, we label the posts as suicidal and nonsuicidal. Through this labelled data, we answer the following research questions:
1) Do the longer narratives of mental illnesses contain more suicidal content as compared to smaller ones?
2) Are individuals discussing about certain disorders tend to write more suicidal content?

# Dataset
1) Reddit_dataset: This analysis centres on posts spanning the past seven years, encompassing the period from 2016 to 2022. The data is collected using Pushshift Reddit API. It is RESTful API that provide the ability to search ‘submissions’ i.e., posts, on reddit by using the search submissions method. The resulting dataset, reddit dataset, has 365,419 rows of data from subreddits: anxiety (43.11%), depression (34.03%), bipolar (9.64%), schizophrenia (3.13%), mentalillness(10.08%).
2) Suicide_dataset: This is the subset of publicly available suicide dataset on hugging face. The rows labelled as ’suicidal’ in this dataset contain reddit posts from the popular subreddit ’SuicideWatch’ which has 434k members. The data was sampled and re-labelled to create the final suicide detection dataset which is used to train our suicidal content detection model. It has of 300 rows of labelled data for training with the total of 129 rows are labelled as ’suicidal’ and 171 are labelled as ’non-suicidal’.

# Model for Suicidal Content Detection
For this particular task, we load a pre-trained Sentence Transformer model, ‘paraphrase-mpnet-base-v2’ from Hugging Face which is a sentence-transformers model that maps sentences and paragraphs to a 768 dimensional dense vector space. Using SetFit framework this model is finetuned on suicide_detection dataset. The accuracy of final model on reddit test dataset is 83%.

# Annotating Posts for each disorder
It can be assumed that the subreddit names suggest a user is talking about a particular disorder, but it’s not always the case. On closer inspection of data, it is observed that even though a subreddit has a certain title, for example ‘depression’, the posts by the users can be about unrelated matters or might even be related to some other disorder. Therefore annotating these posts based on community affiliation is not optimal.
To get the posts where the users are specifically talking about a particular disorder, pre-trained model ‘all-MiniLML6-v2’ from hugging face is used. The model generates
sentence embeddings of all the posts and can be used to tasks like semantic search. Then cosine similarity score is calculated between these embeddings and the query text which contains the disorders.
To label a post the cosine similarity score must be above a threshold. This threshold needs to be determined. For this purpose, an English-speaking human annotator took 420 samples from the dataset and manually identified disorder being discussed on their post for each disorder. For example, if a post discusses how the user is coping with anxiety disorder, it will be labelled as 1 for anxiety disorder.We then calculate Cohen’s Kappa score with various threshold values. The threshold value of 0.36 maximizes the Cohen’s Kappa score for the disorders. The value being above 0.7 for Anxiety disorder, depressive disorder and schizophrenia suggest subtantial agreement between the
model rating in the manual annotation while above 0.8 score for bipolar disorder suggests near ’near perfect agreement’ between model and manual annotation.

# Sentiment Analysis
To assess the sentiment of a posts, we use a pre-trained model called VADER (Valence Aware Dicstionary and Sentiment Reasoner) from NLTK library.

# N-gram Analysis
N-grams provide insights into the co-occurrence and relationships between words. For finding the most frequent ngrams, we use CountVectorizer which converts a collection of
text documents into a matrix of token counts.

# Results

RQ1: The analysis shows that there is more percentage of suicidal content in longer posts and also the longer posts seem to have more negative sentiment. Hence, it shows that the longer mental illness related narratives have more suicidal content as compared to smaller posts.

RQ2: The analysis shows that there is more percentage of suicidal content in posts related to depressive disorder followed by bipolar disorder, schizophrenia and anxiety disorder. The sentiment analysis showed that anxiety disorder had most negative sentiment but from the n-gram analysis it was observed that depressive disorder posts had more suicidal content. Hence, it found that there is higher correlation of some disorders like depressive disorder with suicidal content than other disorders like anxiety disorder.

(Refer to the presentation for details on results and future work.)

