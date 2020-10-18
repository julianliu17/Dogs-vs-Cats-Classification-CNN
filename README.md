![DogvsCat](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/woof_meow.jpg "DogvsCat")
# Dogs vs Cats Classification CNN
**CNN with on the fly image augmentation for classifying images of dogs and cats**

1. Processed 25000 training set images of dogs and cats downloaded from [kaggle](https://www.kaggle.com/c/dogs-vs-cats-redux-kernels-edition/data)
2. Explored image augmentation using Keras' ImageDataGenerator
3. Implemented on the fly image augmentation in CNN model
4. Evaluated final CNN model with 12500 testing set images, also downloaded from [kaggle](https://www.kaggle.com/c/dogs-vs-cats-redux-kernels-edition/data)
5. Modified GUI sourced [from this link](https://data-flair.training/blogs/cats-dogs-classification-deep-learning-project-beginners/) for our model, easy to use and can be used to classify any custom images of dogs or cats

This was an introductory/personal research project into computer vision and deep learning. I learned a ton during this project! Any tips for making my model more robust and less expensive are more than welcome. This was originally a 2013 kaggle competition hosted by kaggle, with the goal of identifying images of dogs and cats with deep learning. 

## File Descriptions
DogsVsCats.ipynb - *Jupyter Notebook with image processing, image augmentation, CNN model and predictions on test set images.*

gui.py - *GUI code for easy classification of any custom dog or cat images, run on your terminal/command prompt with `python3 gui.py`*

model3_dogsvscats_10epochs.h5 - *Final CNN model, load by running `from tensorflow.keras.models import load_model` then `model = load_model('model3_dogsvscats_10epochs.h5')`*

## Resources Used
__Python Version__: 3.8

__Packages__: numpy, pandas, matplotlib, seaborn, tensorflow, keras, sklearn, cv2

__Data Source__: https://www.kaggle.com/c/dogs-vs-cats-redux-kernels-edition/data

__GUI Code__: https://data-flair.training/blogs/cats-dogs-classification-deep-learning-project-beginners/

__Learning Materials__: 
* https://www.youtube.com/watch?v=YRhxdVk_sIs   - Introduction to CNN
* https://www.youtube.com/watch?v=cNBBNAxC8l4   - Convolutional Filters
* https://towardsdatascience.com/deciding-optimal-filter-size-for-cnns-d6f7b56f9363   - Optimal filter size for CNNs
* https://keras.io/api/layers/convolution_layers/convolution2d/   - Keras CNN documentation

## Data Processing and Image Augmentation
I started off with creating a dataframe of our data and plotting a countplot to have a feel for the data, the 25000 images was split 50/50 dogs and cats.

![df_info](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/df_info.JPG "df_info")

![countplot](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/countplot.JPG "countplot")

![split](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/train_test_split.JPG "split")

Then I plotted a few original images of dogs and cats in the dataset.

![preaug](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/dogsandcatspreaug.JPG "preaug")

Here is the code that I ran to augment the original images using `keras.preprocessing.image.ImageDataGenerator` and `.flow_from_dataframe`.

![code](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/imagedatagenerator.JPG "code")

![code](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/traintestdatagen.JPG "code")

After running the code I plotted some augmented images of a random sample in the data. 

![code](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/augmenteddog.JPG "code")


