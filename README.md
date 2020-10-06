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
The method used in this project be able to generate a text sequence is many-to-one sequence model, often used with time series. That means that the most recent sequence of certain length (word sequence) is used to predict the next word.

To transform a text into such a format
Example text:
*Before time was time, there was a Great Hill. And on the Great Hill there lived the Yolks. The Yolks spent their entire lives climbing the Great Hill, trying to reach the top.*

Tokenizing special characters:
*Before time was time //Comma// there was a Great Hill //Period// And on the Great Hill there lived the Yolks //Period// The Yolks spent their entire lives climbing the Great Hill //Comma// trying to reach the top //Period//*

Look up table


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



Sequence size
9

|f1 |f2 |f3 |f4 |f5 |f6 |f7 |f8 |f9 | TARGET |
|---|---|---|---|---|---|---|---|---|--------|
|9|4|5|4|6|7|5|10|1|2|
|4|5|4|6|7|5|10|1|2|3|
|5|4|6|7|5|10|1|2|3|11|
|4|6|7|5|10|1|2|3|11|12|
|...|
|0|1|2|6|19|20|21|0|22|3|






## Contact
* Please visit my [website](https://marketaince.com/).

## Sources
[1] [Recurrent Neural Networks by Example in Python](https://towardsdatascience.com/recurrent-neural-networks-by-example-in-python-ffd204f99470)

[2] [The Great Hill](https://www.freechildrenstories.com/the-great-hill)