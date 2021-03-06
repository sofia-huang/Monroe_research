# Results

To reiterate the objectives for this project, my goal was to generate fake reviews based on Amazon product review data, classify them as either positive or negative and assign an overall rating, then predict whether or not the generated reviews would be considered "helpful". I produced 10 reviews using the GRU Keras model which I trained on the "Kindle Store" subset of the Amazon data [4] with 10 epochs. Below is one of the reviews generated. 

*"The books were going to caught up it with a strong holiday wester series. There are some grammar and twists. I loved this book, but it had moments of bad dialogue. It was miss the story that leaves you hanging right into the story as I started reading the book in the series. I was hooked from judgeous woman of angst and ways outside of that. Which I endone who play!! loved every world they keep getting better. The author made the short story to buy a novella that says it and end, but that's of preparing to come. I don't know if it, I'm looking forward to more of her two paranormal errors, and be read. Oh my god.  Linded hard no matter what to do so. The Saga is a pretty good guy and 4 to help pull other if she wants... the reader safe the sense of being sweet, and she is starting to reach them everything. While it was still going against meetamining onlones and act-as she story putting them out of cohe into a first practical ending. Surpers camp to the couple that, turns, and stay kidnapped an"*

As you can see, the reviews had a few spelling mistakes and although the words were english, the sentences did not make much sense. I believe that if trained on more epochs or a larger dataset, the results would be significantly better. Also, since the dataset consisted of reviews written by humans, there is no gauarantee that words were spelled correctly and proper grammar was used. A graph showing the training loss is shown below. Evaluating a text generation model is tricky and the easiest way is by human judgement. The generated reviews are not ideal and need to be improved on order to appear real. I believe it is a good start and future projects could include refining the model and dataset to obtain better results. 

<img src="line-graph.png" width="450" height="292.5" /> 

Next, I used the 10 reviews generated by the model as input for the text classification model. The results are shown below and the full reviews are at the end of this page with the corresponding number. 4 were classified as positive and 6 as negative. The model had an accuracy of 0.638 which is not satisfactory. I believe that making the generated reviews shorter would improve the results as there would be less opportunity for a mix of positive and negative words to be generated and confuse the classification model. 

<img src="class_pred.png" width="235" height="260" /> 

My last model objective was to test multiple supervised learning models to find the best one for predicting whether or not a review was helpful. After training and testing the various models, I evaluated them using their AUC-ROC score and found that the logistic regression model performed the best with a score of 0.7752 on the test set. To improve the results of the model, I added the overall rating to the feature set. Below is a graph comparing the ROC-AUC score of the LR model with and without the rating.

<img src="roc_curve.png" width="400" height="250" /> 

I fed the generated reviews and their respective ratings, which I assigned based on the classification results, into the logistic regression model. The results are shown in a table below.

<img src="help_pred.png" width="225" height="260" /> 

I believe to improve the model, a bigger data set can be used to train and test on. Also, by refining the text generation model, the results will be more accurate as the reviews will be more similar to actual reviews. For a future project, I would take steps to increase the accuracy of all 3 models such as using a larger dataset, increase epochs, and tune hyperparameters. Results of this project have potential to be used as training data for models to detect fake reviews and feature the highest quality reviews without needing customer feedback which will in turn, enhance online customer experience. 

[10 Generated Reviews](gen_rev.md)

### [Back to Main Page](index.md)
