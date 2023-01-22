# Sentiment-Analysis-of-Tweets

The repository contains the data & code for detecting the sentiments from tweets using Deep Neural Network.

## Datasets

I used the publicly available labelled dataset of approx 162K Tweets on [Kaggle](https://www.kaggle.com/datasets/saurabhshahane/twitter-sentiment-dataset) 

The label -1 represents Negative sentiment, 1 represents Positive sentiment and 0 represents Neutral sentiment.

The below figure represents the distribution of data among each category.

You are supposed to see the data used in `Data` folder

![data_distribution](https://github.com/Mayurwaghela1997/Sentiment-Analysis-of-Tweets/blob/main/Data/data-distribution.PNG)

## Data Preprocessing

The dataset includes total of 162980 rows.
After removing the rows having null values, I left with 162969 rows.

Train(60%), Validation(20%), Test(20%) splits are used for the model training & evaluation.

### Removing english stop words & Lemmatizing

I used NLTK english stopwords to remove the stopwords from the tweets.
Lemmatization, One of the most important steps in Natural Language processing is changing the word to it's root form.
For e.g. the Lemma of word 'feet' will be 'foot'.
For lemmatizing, NLTK's WordNetLemmatizer is used. 

### Tokenization

First, Keras Tokenizer has been trained on the training dataset and then the trained tokenizer is used to create sequences of training, validation and test set. 
We use oov_token '<UNK>' for the out of corpus tokens and filters to ignore speical characters.

### Padding & Truncating sequences
  
for padding and truncating post method is used it means it will add or remove the required data at/from the end of the sequence.

The below figure shows the distribution of lenghts of sequences in training set.
  
![tweet_length_distribution](https://github.com/Mayurwaghela1997/Sentiment-Analysis-of-Tweets/blob/main/Data/tweet-length-distribution.PNG)

We can see that the maximum length of sequence is 43, so we keep 45 as max length while padding or truncating sequences.
  
## Model

RNNs/LSTMs have shown great results in the field of Natural Language Processing(NLP).
For the purpose of sentiment analysis, the model architecture utilzes BiDirectional LSTMs. 

The comepletle model architecure of model can be seen in below image.

![data_distribution](https://github.com/Mayurwaghela1997/Sentiment-Analysis-of-Tweets/blob/main/model-architecture.PNG)


## Results

The results of the sentiment alanysis is under `Results` folder.
 
During the training, The model fits well to training data and we can see the loss getting reduced.
The call back was set to 3 patience on validation_accuracy while training so the model stopped learning at 5 epochs.
The below figure represents the training history in terms of accuracy and loss.
![Training-history](https://github.com/Mayurwaghela1997/Sentiment-Analysis-of-Tweets/blob/main/Results/training-history.PNG)

### Evaluation

The trained model was evaluated using test set and the accuracy on test set was 86%.

The below figure represents the confusion matrix from sklearn.



