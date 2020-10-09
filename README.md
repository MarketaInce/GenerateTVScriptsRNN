# *TV Script Generator* - Recurrent Neural Network

This project is a part of [Deep Learning Nanodegree](https://www.udacity.com/course/deep-learning-nanodegree--nd101) by [Udacity](https://www.udacity.com/).

*Submitted: Aug 2019*

## Objective
The purpose of this project is to create a neural network that generate a **new** TV script for [Seinfeld](https://en.wikipedia.org/wiki/Seinfeld) sitcom.

### Methods Used
* Recurrent Neural Network (**RNN**)
* Long Short Term Memory (**LSTM**)
* Pattern Recognition
* Many-to-one sequence mapper

### Technologies
* Python
* PyTorch

### Training Data
The data used to train this RNN is [Seinfeld Chronicles](https://www.kaggle.com/thec03u5/seinfeld-chronicles#scripts.csv) transformed into a *.txt* file. The original dataset available on [Kaggle](https://www.kaggle.com/) contains scrips from all seasons of this sitcom and is available in form of a *.csv* file.

## Project Description
The method used in this project be able to generate a text sequence is many-to-one sequence model, often used with time series. That means that the most recent sequence of certain length (word sequence) is used to predict the next word. For that the text has to be transformed into a similar format.

In the following example such a transformation is demonstrated.

**Example text**:

> *Before time was time, there was a Great Hill. And on the Great Hill there lived the Yolks. The Yolks spent their entire lives climbing the Great Hill, trying to reach the top.*

#### 1. Tokenizing Special Characters
Special characters have to be replaced by defined tokens so that they can be used for training:

> *Before time was time //comma// there was a Great Hill //period// And on the Great Hill there lived the Yolks //period// The Yolks spent their entire lives climbing the Great Hill //comma// trying to reach the top //period//*

#### 2. Look-up Table
Look-up table is created based on text with tokenized special characters. Each word or token is assigned and index staring from 0:

|INDEX   |WORD      | INDEX   |WORD      | 
|---------|-----------------|---------|-----------------|
|0 | 'the'|12 |'on' |
|1 | 'great'|13 | 'lived'|
|2 | 'hill'|14 | 'spent'|
|3 | '//period//'|15 | 'their'|
|4 | 'time'|16 | 'entire'|
|5 | 'was'|17 | 'lives'|
|6 | '//comma//'|18 | 'climbing'|
|7 | 'there'|19 | 'trying'|
|8 | 'yolks'|20 | 'to'|
|9 | 'before'|21 | 'reach'|
|10 | 'a'|22 | 'top'|
|11 | 'and'|

#### 3. Features and Target
If the chosen sequence length would be **9** (9 words or tokenized special character) the text would be parsed in the following manner.

> *before time was time //comma// there was a great hill*

First 9 words is the first sequence for feature matrix.
 
| before: 9 | time: 4 | was: 5 | time: 4 | //comma//: 6 | there: 7 |  was: 5 | a: 10 | great: 1 |
|---|---|---|---|---|---|---|---|---|

The 10th word is the target for first sequence.

| hill: 2 |
| --- |

With each sequence we move one word ahead in the text. That means for the second sequence of the text to be parsed would be:

> *time was time //comma// there was a great hill //period//*

The whole text is parsed in the same manner until it's end, where each sequence corresponds to one row of Feature matrix and target column:

|f1 |f2 |f3 |f4 |f5 |f6 |f7 |f8 |f9 | TARGET |
|---|---|---|---|---|---|---|---|---|--------|
|9|4|5|4|6|7|5|10|1|2|
|4|5|4|6|7|5|10|1|2|3|
|5|4|6|7|5|10|1|2|3|11|
|4|6|7|5|10|1|2|3|11|12|
|...|
|0|1|2|6|19|20|21|0|22|3|


#### 4. Training

As mentioned above the model is trained to be able to predict the most probable word that should follow a given sequence of words. The technology used here is a Recurrent Neural Network. More information about this type of NN visit [Recurrent Neural Networks by Example in Python](https://towardsdatascience.com/recurrent-neural-networks-by-example-in-python-ffd204f99470).

#### 5. Results

To get a prediction a starting word must be provided, for the model to be able to determine the next most probable word. We can continue getting a new prediction in a loop until we reach the requested text length. The example below was generated with a starting word:

> *elaine*

| ![TV Script Generator - result example](<src/results.jpg>) |
| --- |

## Contact
* Please visit my [website](https://marketaince.com/).

## Sources

[2] [The Great Hill](https://www.freechildrenstories.com/the-great-hill)