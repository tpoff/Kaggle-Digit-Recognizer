# <b>Kaggle MNIST Digit Recognizer.</b>
## <b>Pytorch CNN with Data Augmentation and Model Ensembling</b>
This repository contains the training notebook/project overview notebook, final trained models, and submission csv for the Kaggle
MNIST Digit Recognizer Compitition. [Link to the Kaggle Compitition](https://www.kaggle.com/competitions/digit-recognizer)

The MNIST dataset is a well known dataset for computer vision consisting of thousands of hand drawn samples of the digits 0-9. 
The goal of the dataset is to build a model that can accurately predict the digit depicted in the image. 

Using pytorch I first built a CNN base model with 6 CNN layers and 2 FC layers that can predict to about 99.3% accuracy. A respectable score but we can do better.

Next I used data augmentation to create more variation for the training data. Data augmentation is the process of randomly adjusting the inputs to create a similar but still different sample. For this project
I used scaling, rotating and adjusting the image contrast to provide some variation in the dataset. This process allows the model to better generalize and not just memorize the training data. A 3 is a 3 even if it's tilted a bit, and letting the model
train on both variations allows it to get the concept of a 3 rather than just trying to memorize a particular instance of a 3. With Data Augmentation I reach a score of about 99.6%. 

The final step is ensembling. I trained 40 models for 30 epochs each, using the base CNN model and the data augmentation each time. Due to the randomness of starting weights and
the randomness of the data augmentation this provided 40 unique models that are each slightly different. Meaning each model has their own strengths and weaknesses. I then selected the top 10 performing models (based on the final score of the entire training set)
and ensembled them together. In essence allowing each of the top 10 models a "vote" on what they believed the label should be. Using this ensembling you allow the models to cover individual weaknesses, where 1 model might predict wrongly the other 9 might predict correctly, 
leading to a correct classification. Using this technique I boosted my top score to 99.68%, which is what I believe the final score for this project should be.

It is worth noting, that I did continue exploration after achieving this score. By selecting random models from the pool of trained models I was able to achieve an ensembled score of
99.7%. This showed that the best models to ensemble are not always the top performing models, but rather models that more deliberately compliment each other. By selecting models based on which perform poorly and which models help make up for that lacking performance you
can achieve a much higher score. I don't consider this 99.7% the true final score as I found it through random chance, however in the future I will keep this lesson in mind and find more
meaningful ways of selecting models to ensemble for future projects. 

For more details on the training process, results, and lessons learned, please check out the included notebook. It goes over the concepts more in depth and walks through the training process used to
build the models. 