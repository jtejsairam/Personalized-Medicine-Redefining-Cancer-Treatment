## Personalized-Medicine-Redefining-Cancer-Treatment
In this project, we will develop machine learing model to classify genetic mutations based on clinical evidence (text). There are nine different classes a genetic mutation can be classified on. This is not a trivial task since interpreting clinical evidence is very challenging even for human specialists/expert. Therefore, modeling the clinical evidence (text) will be critical for the success for our approach.

## Data Description
<b>training_variants</b> - A comma separated file containing the description of the genetic mutations used for training. Fields are:<br> 
<b>ID</b> - (the id of the row used to link the mutation to the clinical evidence)<br>
<b>Gene</b> - (the gene where this genetic mutation is located)<br>
<b>Variation</b> - (the aminoacid change for this mutations)<br>
<b>Class</b> - (1-9 the class this genetic mutation has been classified on)<br>

<b>training_text</b> - A double pipe (||) delimited file that contains the clinical evidence (text) used to classify genetic mutations. Fields are:<br>
<b>ID</b> - (the id of the row used to link the clinical evidence to the genetic mutation)<br>
  <b>Text</b> - (the clinical evidence used to classify the genetic mutation)<br>

<b>Source:</b> https://www.kaggle.com/c/msk-redefining-cancer-treatment/

Download the data(training text, training variants) from here-> https://www.kaggle.com/c/msk-redefining-cancer-treatment/data

<b>Data:</b> Memorial Sloan Kettering Cancer Center (MSKCC)

Context Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/discussion/35336#198462

## Problem Statement
Classify the given genetic variations/mutations based on evidence from text-based clinical literature.

## Summary of the problem's solution
  * First of all we will download data from the source and load the data into pandas dataframe. 
  * Found that some special char, multiple space b/w words so used text preprocessing/data cleaning.
  * Did EDA for better understanding of data and found that some insights out of it although It is medical data and for better understanding of data we need to have some good knowledge in molecular biology or to be more specific domain knowledge.
  * Extracted some feature out of text data as well as from the others features(Gene, Variation) also and did some visualization to understand whether it has some value or not.
  * checked for distribution of the class labels among train,test, and validation data. 
  * After this, built a random model and generated 9 class probability randomely such that they sum to 1 to ensure that whatever model we built on top of this the loss will be always less and got log-loss ~2.5 from this random model.
  * Featurized categorical feature into numerical using onehotencoding and response coding and used both featurized vector to predict class label.
  * built other models with each and every individual engineered feature and check for whether they will be helpful or not in prediction and found that they are helpful. 
  * On the text features, used bow and tfidf and choose top 3k features and then stacked all the features on top of each other.
  * Now it's time to build model but before we built, first tuned the hyperparameter and then started with baseline model naive bays and obtained train loss ~ 0.9, test loss ~1.15 and validataion loss ~1.9.
  * And then again tuned hyperparameter for nearest neighbor and got slightly better or same accurcy than naive bays.
  * Tried naive bayes, nearest neighbor, logistic regression, linear SVM, random forest, stack 3 models(logistic regression, linear svm, naive bayes) and then used voting model and for each and every model did hyperparameter tuning, showed % of missclassified point, showed confusion matrix, precision, recall in a heatmap and the most important given interpretation(i.e. why the given gene and mutation comes under class 4 or whatever) for each model.
  

