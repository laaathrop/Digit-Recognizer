<div align="center">
  <img src="https://acroz.dev/public/nn/mnist-digits.svg"><br>
</div>

-----------------

# Digit-Recognizer: powerful KNN classifier for MNIST digits

## What is it?
The Digit-Recognizer is a powerful k-nearest neighbors classifier designed to illustrate the power and simplicity of gridsearching over hyperparameters and chaining transformers with estimators in a pipeline using scikit-learn.

## Main Features
Main points of the project:

  1. Objective
  2. Data Description
  3. Exploratory Data Analysis (EDA) & Visualization
  4. Preprocessing, Modeling and Evaluation
  
## Technical Summary

The MNIST data set is a learning tool used for exploring machine learning and computer vision fundamentals. It is a subset of an even larger repository of images available from NIST. The primary objective of this project is to use this data set along with the k-nearest neighbors algorithm to classify images in this data set by separating the pixel data from the labels, training a model on the pixel data, and then using the model to predict labels based on pixel data alone. The secondary goal for this project is to generate predictions based on the testing data provided by the Digit Recognizer Kaggle competition, submit them to Kaggle and see the results.

Each image corresponds to one row in the .csv files provided by the Kaggle competition. Each row contains a label column and 784 pixel columns, one pixel for each of the images, which are 28x28=784 pixels in size. Each of the pixels can have a value in the range [0, 255] (the brackets here are intended to denote inclusivity of the minimum and maximum values). Pixel values are integers and the higher the magnitude, the darker they will be. The training data provided is a set of 42,000 labelled images, the testing data is a set of 28,000 unlabelled images from the training set. Categorization accuracy was used to evaluate the model and represents the proportion of images that were correctly classified.

The data was explored first for consistency with the data description provided by Kaggle (https://www.kaggle.com/c/digit-recognizer/data). No inconsistencies were found. The data was explored via visual inspection, value counting, data masking and image visualization. Counting the label values showed that the classes were approximately balanced. Inspecting multiple images of a single digit showed some variation in the pixel shades and pixel locations for images displaying the same number. The assumption at this point in the project was that images displaying the same number may have been inscribed by different people and thus resulted in the image variations. This assumption was later confirmed by plotting (3) of the digit 9. This showed that each of the the visualized number 9 did indeed look different: For example, when inspected closely, the loop and trunk of the number 9 both appear to be a slightly different size and shape in each image. The line thickness also varies, probably depending on the instrument used to inscribe the image.

The modeling stage kicks off by defining a function to ease the process of tuning the model and varying the quantity of images used to train the model. The function accepts a pipeline and a parameter grid in order to perform a search over the estimator provided, in this case, k-nearest neighbors. The data was also scaled so that the pixel values would fall within the range [0, 1]. Some trial and error resulted in parameters that were fed into gridsearch. The next goal was to establish a trend between the number of cross validation (CV) folds and the accuracy of the model because initial stage models suggested that increasing CV folds would improve model accuracy. For 1000 and 5000 data points, CV folds were varied from [2, 25]. Accuracy data was gathered for each of these cases and visualized. The shape of the plots seemed suggest a logarithmic or positive trend between the number of CV folds and the best score produced by gridsearch for both cases (1000 and 5000 images). However, positive trends between the number of CV folds and testing accuracy seemed to only exist for n_images=1000 for low values of CV. Because of this observation, I conservatively chose the number of CV folds to be 10 because it is a happy medium considering the tradeoff between processing time and accuracy improvement while varying the number of CV folds. 

Note: The final accuracy score will be located in the jupyter notebook in Modeling - Phase 2, observations will be added once the final code executes.

## Source Code
The source code is currently hosted on GitHub at:
https://github.com/laaathrop/Digit-Recognizer

## Dependencies
- [Kaggle](https://www.kaggle.com/c/digit-recognizer/)
- [pandas](https://pandas.pydata.org/)
- [seaborn](https://seaborn.pydata.org/)
- [matplotlib](https://matplotlib.org/3.3.2/index.html)
- [scikit-learn](https://scikit-learn.org/stable/index.html)

## Background
The initial stages of this classifier were completed while working through the curriculum of General Assembly's Data Science Immersive program. My work at General Assembly helped me lay the foundational skills in Data Science and Machine Learning that I continue to develop to this day.

## Discussion and Development
Feel free to send me an email at Anthony.Lathrop@outlook.com with questions, comments or points of discussion. I am always open to connect and chat about Data Science and Machine Learning!