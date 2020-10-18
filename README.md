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

