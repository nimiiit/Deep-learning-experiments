# Convolutional Classifiers

We start with a basic Convolutional classifier (CNN) for binary classification on dog vs cat dataset. We then check the concept of label smoothing introduced in literature for improved accuracy and overcoming the model issue of overconfidence.

Listing good reads on label smoothing:

* Paper:  https://arxiv.org/pdf/1512.00567.pdf
* Blogs: https://towardsdatascience.com/label-smoothing-making-model-robust-to-incorrect-labels-2fae037ffbd0 , https://rickwierenga.com/blog/machine%20learning/LabelSmoothing.html

     
## Label smoothing:
When a network is trained for classification, we observe that after training even if we pass some data which is not from a class it was trained for, the network still predicts wrong label with a high confidence. This is even true for any wrong classification in general.
Hence the confidence (final output after softmax or sigmoid) does not reflect well on the classification outcome. The model is not calibrated well to handle misclassification. There are works in overcoming this high confidence issue using Temperature scaling etc.

Label smoothing is yet another way to overcome model overconfidence. Instead of training the network with hard codes (like 0 or 1 in case of binary classification), label smoothing uses a soft codes (0.1 and 0.9). The assumption is that by doing this it  gives a flexibility of 10% error in the data labels while training itself. Hence instead of highly confident during training, there is a 10% uncertaininty now. This makes the predictions also (on the test set) to be not overconfident.

Papers claim that there is an improvement in accuracy as well with label smoothing.

## What this code contains:

* We start with defining a CNN based binary classifier
* Use the do-cat dataset 
* Define the data augmentations, and network hyperparameters
* Train a model with hard labels (0 and 1)
* Now change the labels to soft labels (0.1 and 0.9) and retrain the network

--  Observation: When the histogram of true dogs vs false dogs (cats misclassified as dogs) is plotted, we observe that without label smoothening the false dogs confidence are near to the true dogs (i.e there are cats being predicted as dogs with high confidence).
But with label smoothing the false dogs confidence is more centered to 0.5 rather than 1. But we also notice that the overal confidence of true dogs also come down from 1. 

-- Histogram of true dogs vs false dogs before label smoothing : The blue values are true dogs and orange the false dogs. You can see that there are false predictions with confidence ranging from 0.5 to 1. (Since its binary classification predictions >0.5 are considered as class dog)

<img src="histogram_before_ls.png?raw=true" width="300px">

--Histogram of true dogs vs false dogs after label smoothing :  We can see that the blue plots are no more concentrated on 1 (i.e the confidence of true dogs also goes low) and the confidence on wrong predictions are now more towards 0.5 (i.e the network is not overconfident on the wron predictions which is GOOD !!!)

<img src="histogram_after_ls.png?raw=true" width="300px">

Another observation was that there was no much improvement on accuracy after label smoothing. May be the dataset is good enough and models are good. So to verify if label smoothing handles mislabeling in data, next thing I did was to manually introduce errors in the ground truth labels before training.

* Introduced error in ground truth labels and then trained networks with and without label smoothing. 

--Observation: There was not much improvement in accuracy after label smoothing as we expected. May be we need to explore more on new multiclass data to validate the claims in paper.


Cheers !!!!  Try out few and let me know as well !!!!!!!!!!!!!!!!!!!!!!!!!!!! 
