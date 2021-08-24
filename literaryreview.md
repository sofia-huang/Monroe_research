# Literature Review

1. [Amazon Product Review Dataset](https://nijianmo.github.io/amazon/index.html#subsets)

2. [Tensorflow Text Generation Tutorial](https://www.tensorflow.org/text/tutorials/text_generation)

3. [NLTK Learning to Classify Text](https://www.nltk.org/book/ch06.html)

4. [Predicting the Helpfulness of Amazon Reviews](https://www.cs.dartmouth.edu/~lorenzo/teaching/cs174/Archive/Winter2015/Projects/finals/ack.pdf)

This was the primary research paper I used as reference for the helpfulness classification model. As I read through the paper, I took note of the preprocessing steps they used on the data before inputting into the model for training. They used the two most correlated aspects of a review, overall rating and review length, as part of the feature vector. Then, they filtered the reviews to only include those with at least 30 words and 10 votes to make sure reviews that have not been voted on do not skew the training or testing sets. A vocabulary was built from the n most frequent stemmed words after applying a Porter Stemmer to the review texts. Finally, they extracted features using the same Porter stemmer to obtain the vocab word presence of the review text, as well as the rating, cost, and length of the reviews. In this paper, they used Random Forest Regression to predict the helpfulness scores of the reviews. Their justification was that it was faster and just as accurate as other common models. I took these preprocessing steps into consideration when preparing the data for my own model in order to increase the accuracy of the classification.
