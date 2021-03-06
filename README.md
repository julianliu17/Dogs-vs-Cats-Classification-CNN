![DogvsCat](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/woof_meow.jpg "DogvsCat")
# Dogs vs Cats Classification CNN
**CNN with on the fly image augmentation for classifying images of dogs and cats**

1. Processed 25000 training set images of dogs and cats downloaded from [kaggle](https://www.kaggle.com/c/dogs-vs-cats-redux-kernels-edition/data)
2. Explored image augmentation using Keras' ImageDataGenerator
3. Implemented on the fly image augmentation in CNN model
4. Evaluated final CNN model with 12500 testing set images, also downloaded from [kaggle](https://www.kaggle.com/c/dogs-vs-cats-redux-kernels-edition/data)
5. Modified GUI sourced [from this link](https://data-flair.training/blogs/cats-dogs-classification-deep-learning-project-beginners/) for our model, easy to use and can be used to classify any custom images of dogs or cats

This was an introductory/personal research project into computer vision and deep learning. My goal from this project was to familiarize myself with deep learning and computer vision techniques. I learned a ton from this project! Any tips for making my model more robust and less expensive are more than welcome. This was originally a 2013 kaggle competition hosted by kaggle, with the goal of identifying images of dogs and cats with deep learning. 

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

## Model Building
I started by building a base model and running with 3 epochs, which took surprisingly long. This base model had an accuracy of 71%.

![base model](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/basemodel.JPG "base model")

For my second model I added batch normalization, dropout and a 512 Dense layer after flattening. I also added early stopping and learning rate reduction with `from keras.callbacks import EarlyStopping, ReduceLROnPlateau`. However, I realized after running the model that I set `monitor = 'val_acc'` instead of `monitor = 'val_accuracy'`, so I don't think the learning rate reduction worked. This model only improved slightly from the base model after 3 epochs and after 10 epochs it had an accuracy of 80.7%. 

![improved model](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/improved%20model.JPG "improved model")

Finally, I added an extra Conv2D layer and more dropout layers to my final model. This model achieved an accuracy of 82% after 10 epochs. For some reason, my models ran for a long time (2/3 hours), perhaps because my image size (200x200) and batch sizes (100) were too large and small respectively for my computer. 

![final model](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/finalmodelcode.JPG "final model")

![final model](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/finalmodelsummary.JPG "final model")

![final model](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/modelperformanceviz.JPG "final model")

As can be seen from the training and validation accuracy and loss graphs, our model is still improving after 10 epochs, therefore it can be argued that my model should be able to perform better than 82%. Nevertheless, I didn't want to run my models for longer as I was pleased with my model's performance after testing it with custom images on the GUI classifier.

Here are some examples of the predictions made by the model using the test set of 12500 images.

![final pred](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/finalpredictions.png "final pred")

Not bad at all! In this sample size of 18, the model only misclassified 1/18 (5%).

## GUI

To run gui.py, follow the steps below.

![guidemo](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/guistart.JPG "guidemo")

![guidemo](https://github.com/julianliu17/Dogs-vs-Cats-Classification-CNN/blob/main/Pictures/guidemo.JPG "guidemo")

## Project Evaluation
Overall, the main goal of this project has been met. The main goal was to familiarize myself with deep learning and computer vision techniques. Although the accuracy of my final model wasn't in the 97-99% territory, the model was still improving after 10 epochs so perhaps it could reach 90% after a few more epochs. 

I ran some predictions with some custom images both downloaded from the internet and photos from friends, and it did not disappoint! It was very accurate when classifying unseen images. However, one thing I would like to address in the future is the slow speed when fitting my model. I could definitely look into optimizing the speed of my code such as playing around with the image size and batch size, as well as trying to classify without image augmentation.

That's it for this project, thanks for making it this far!
