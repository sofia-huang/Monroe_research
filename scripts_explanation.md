# Explanation of the Models

## Dataset
For this project, I have chosen to use a dataset of Amazon product reviews by Julian McAuley of UCSD [4]. I decided to use the "Kindle Store" subset due to its size and my computers conputational power. Each entry in this dataset represents a review. Below is an example of a review and its fields. The fields I will focus on are "helpful", "reviewText", and "overall".

<img src="sampleReview.png" width="525" height="214.5" /> 

Notice the "helpful" field is a tuple of two integers. The first being the number of upvotes on a review and the latter being the total number of votes on a review. This is important for the helpfulness classification model.


## Text Generation
I used the Tensorflow RNN text generation tutorial [6] as a basis for this model. First, I downloaded the text file that I preprocessed for the classification model. Then, I vectorized the text, meaning converted them from text data to numerical representations. This RNN model is character-based, so given a chracter it will predict the next probable character. To create the training and testing sets, I created sequences of text with a length of 100. These are the input sequences and the corresponding target is a sequence of the same length shifted over one character to the right. Next, I created trainig batches with the shuffled data to feed into the model. The actual model is a Keras model with a GRU layer. GRU stands for "Gated Recurrant Unit" and I chose this over an LSTM model because it is simpler to use and faster on smaller training sets. Below is the model summary.

<img src="textgenModel.png" width="435" height="195" /> 

I attached an optimizer and loss function to the model and configured checkpoints before training the model on the data. I used 10 epochs as that was what my computer was capable of. After training the model, I generated the reviews by running the model through a loop and saved them to a text file.

## Text Classification
I used NLTK's Naive Bayes classifier for this model because it seemed to be the prefered model for text classification. The purpose is to classify a review as either positive or negative. First, I downloaded the data from online and converted it to a dataframe. Then, I removed all reviews with no text and those with 3 stars since those are neother positive or negative. I also removed all unnecessary columns which left just the overall rating and the review text. Once I filtered the reviews, I saved them to a text file for use in the text generation model. Next, I created positive (>3 stars) and negative (<3 stars) review lists of equal lengths. I cleaned the lists by making them all lowercase and removing stopwords and punctuation. Then, I made lists of positive and negative words to become feature sets for the model. I combined the feature sets and split them into training and testing sets and trained the model. Finally, I inputted the generated reviews and classified them as either positive or negative. 

## Helpfulness Classification
I tested various supervised learning models from sklearn to see which was the most accurate in order to predict whether or not a review is helpful. I started by downloading the data and converting it to a dataframe. I then removed unnecessary columns and split the "helpful" column into the numerator and denominator. I also got rid of reviews that had less than 10 votes as they do not have enough user input to be classified as helpful or not. I created a new "Helpfulness" column that contained a binary value with a 0.5 threshold for the ratio between the numerator and denominator. 0 being not helpful and 1 being helpful. I cleaned the text data and made it all lowercase, removed punctuations, tokenized it, removed word stems, vectorized it, and created a feature set. Then, I split the data into training and testing sets to evaluate model performance. 

I used helper methods to train and test each model: Gaussian Naive Bayes, Adaboost, Random Forest, Logistic Regression, and Decision Tree. I evaluated them based on their AUC-ROC score which is the area under the Receiver Operating Characteristic Curve from prediction scores. I chose the one that performed the best and added one more feature, the overall rating of reviews. I trained and tested the best performing model one more time with the added feature and used grid searching to find the optimal hyperparameters. Once I found the model that worked the best, I inputted the generated reviews with their respective overall ratings which I computed from the text classification results. If a review was classified as positive, it got 4.5 stars (classified as either 4 or 5 so I chose to use the average), and negative recieved 1.5 stars (classified as either 1 or 2 so, again, I chose to use the average). Lastly, using the best model I found, I predicted if the generated reviews would be helpful or not.

### [Results & Conclusion](conclusion.md)

### [Back to Main Page](index.md)
