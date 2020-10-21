<div align="center">
  <img src="https://acroz.dev/public/nn/mnist-digits.svg"><br>
</div>

-----------------

# Digit-Recognizer: powerful KNN classifier for MNIST digits


## What is it?

The digit recognizer is a powerful K Nearest Neighbors classifier designed to illustrate the power and simplicity of gridsearching over hyperparameters and chaining transformers with estimators.


## Main Features
Main points of the project:

  - Section 1 of table of contents (In Development).
  - Section 2 of table of contents (In Development).
  - Section 3 of table of contents (In Development).


## Source Code
The source code is currently hosted on GitHub at:
https://github.com/laaathrop/Digit-Recognizer


## Dependencies
- [pandas](https://pandas.pydata.org/)
- [seaborn](https://seaborn.pydata.org/)
- [matplotlib](https://matplotlib.org/3.3.2/index.html)
- [scikit-learn](https://scikit-learn.org/stable/index.html)


## Background
The initial stages of this classifier were completed while working through the curriculum of General Assembly's Data Science Immersive program. My work at General Assembly helped me lay the foundational skills in Data Science and Machine Learning that I continue to develop to this day.


## Discussion and Development
Feel free to send me an email at Anthony.Lathrop@outlook.com with questions, comments or points of discussion. I am always open to connect.

## Technical Summary

This was an exciting assignment for me to complete because it was a chance during the 12 weeks of DSI when I could apply skills I have been learning to a problem of my choice. I have a budding interest in robot perception and robot learning and have been looking for a chance to explore my interest in the context of machine learning and data science. I chose the MNIST dataset in the context of the Kaggle competition with the goal of developing a digit recognizer by applying K-Nearest Neighbors and Support Vector Machines to a computer vision problem, very exciting because of the potential for a real world application in my field of interest. 

After loading the dataset I realized that it was pretty large, about 42000 rows. This is a huge amount of data and hung up my computer several times when I got to the modeling stage. I performed some logical masking on the dataframe containing the set in order to get a feel for exactly what I was looking at. Each data point consists of a label (a single digit between 1 and 10) and 783 additional columns; each one contains a number between 0 and 255 that describes the shade of the pixel. The dataset classes turned out to be very well balanced and there were no unexpected or missing values. 

At first, my intent was to visualize the data by grouping data points of the same labels together and comparing the magnitude of the nonzero integers repesenting each pixel.

My goal when approaching this dataset was to gain some exposure to concepts in computer vision, a very exciting topic considering all of the research being done on self driving cars as well as smart homes, another potential interest of mine. 

Initially I started out with all 42000 rows of the MNIST data and that proved to be way too much for my laptop to handle! In order to make my laptop cooperate I downsized considerably, to about 2000 datapoints. My thought process here was to first establish a baseline. I found cross validation scores for five KNN models with k = 1, 3, 5, 10 and 15, all with five cross validation folds. The accuracy scores here were highest for k = 1, 3 and 5 so these were the values that I ended up putting into my parameter grid when it came time to do gridsearching. The MNIST database of handwritten digits (http://yann.lecun.com/exdb/mnist/index.html) indicated some pretty low error rates for KNN algorithms applied to this dataset, especially for higher values of the power metric, hence my motivation to gridsearch over the top-performing values of k and power metric values. Establishing a pipeline to feed into the GridSearchCV function with these parameters yielded drastically better results, although the model seems to be overfit. I chose to then implement a support vector machine because of its soft margin property inherent to the SVM algorithm; this yielded excellent results. My thought process was that pixels in digit image data will generally not have a clear boundary for classification; a soft margin classifier is needed. The result was less overfitting and a higher overall testing score.