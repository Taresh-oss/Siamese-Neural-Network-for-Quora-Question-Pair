# Siamese-Neural-Network-for-Quora-Question-Pair

### Why Siamese Neural Network?
Quora search engine redirects to different discussion pages based on the search terms searched by the user. So, when questions that are semantically similar are searched on Quora,
it sometimes redirects a user to different discussion pages even if there exists a page to the dedicated search. In such a case, Semantic Similarity among the questions carries 
highest weightage. So, for text, using traditional methods for calculating similarity, usually the text is considered as sequence of words and they just count the number of words 
that occurred in a sentence, on which some distance measures are applied to find the similarity, while missing the semantic level knowledge of the text during calculation. Considering 
such traditional methods, it will also require a huge training set as well as time to produce an accurate model wheras Siamese Neural network can train itself on single instance
of each class which makes it better for such types of problems, as text has a lot of variations but they might mean the same and its impossible to train each one of those possibilties.

### Dataset
Quora has released a public dataset composed of 404, 351 sentence pairs for January 2017. The pairs of questions are from a number of areas, including electronics, entertainment, 
Politics, society, ideology. This dataset is being downloaded from Kaggle . Each record has a pair of questions, A goal class that represents whether or not the questions are 
duplicated. I have used that public dataset only for training and testing purpose.

This public dataset can be downloaded from the link provided:
https://www.kaggle.com/quora/question-pairs-dataset
Details regarding the columns, type of values in columns and number of instances is provided in the link itself.

### Overall Model Architecture and Components

Thae image given below is just an overview of the overall model structure for calculating similarity between the question pairs present in the dataset.

![image](https://user-images.githubusercontent.com/61029579/114500413-f7b41880-9bf5-11eb-85d6-2ddf4ca01c83.png)

The major coomponents of the arechitecture are:

- Word Embedding Layer
- LSTM Layer
- Dense Layer

Before sending the model for embedding, the data is preprocessed. Those preprocessing steps are:
- Converting Text to Lower Case
- Removal of symbols and special characters like ^,*,(,/ etc.
- Lemmatization
- Tokenization
- Padding the tokenized questions

Further step is to embed the preprocessed data, for which I have used pre trained word embedding models which are word2vec and Glove. Link for downloading those pretrained models is provided below:

Glove : https://www.kaggle.com/incorpes/glove6b200d

Word2vec : https://github.com/mmihaltz/word2vec-GoogleNews-vectors

Now for LSTM layer I have three different variations :
- Normal LSTM
- Manhattan LSTM
- Manhattan LSTM + Attention (New Model)

For adding the attention layer I referred to : https://www.analyticsvidhya.com/blog/2019/11/comprehensive-guide-attention-mechanism-deep-learning/

I have tried different combinations of embedding models and LSTM models to come out with the best possible model for similarity measure. The coedes of each such combination has already been added.


