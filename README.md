# Image-Classification
This is an application for Image classification of natural sceneries

# Intel Image Classification
## Image Scene Classification of Multiclass

- Dataset can be found at https://www.kaggle.com/puneet6060/intel-image-classification

### Context
- This is image data of Natural Scenes around the world.

### Content
- This Data contains around 25k images of size 150x150 distributed under 6 categories.
{'buildings' -> 0,
'forest' -> 1,
'glacier' -> 2,
'mountain' -> 3,
'sea' -> 4,
'street' -> 5 }

- The Train, Test and Prediction data is separated in each zip files. There are around 14k images in Train, 3k in Test and 7k in Prediction.


Here are a few example images from each class:

|Buildings	|Forest	|Glacier|Mountain|Sea|Street|
|---	|---	|---	|---	|---	|---    |
|![building](figures/10176.jpg)|![forest](figures/10186.jpg)|![glacier](figures/10256.jpg)|![mountain](figures/11023.jpg)|![sea](figures/10420.jpg)|![street](figures/10112.jpg)


As you can see, not all images are color (although the vast majority happen to be) and there are some unique augmentations to some images as you can see here with the sea image.  One tricky thing about this classification will be getting our model to distinguish between buildings and streets, given that there are usually buildings in the street images and also distinguishing between glaciers and mountains, since these also often look similar.  


## DataSet Navigation

├── <data>
│   ├── seg_train
│   │   ├── buildings
│   │   ├── forest
│   │   ├── glacier
│   │   ├── mountain
│   │   ├── sea
│   │   ├── street
│   ├── seg_pred
│   │   ├── buildings
│   │   ├── forest
│   │   ├── glacier
│   │   ├── mountain
│   │   ├── sea
│   │   ├── street
│   ├── seg_test
│   │   ├── buildings
│   │   ├── forest
│   │   ├── glacier
│   │   ├── mountain
│   │   ├── sea
│   │   ├── street
│   ├── seg_pred

Note the nested nature of the file structure here.  There are duplicate sets of `seg_test`, `seg_train` and `seg_pred` folders within the first sets of these folders.  Be sure to only copy the second nested versions of `seg_test`, `seg_train` and `seg_pred`.

## Modeling

(.ipynb), a convolutional neural networks model using a basic keras Sequential model with Dense layers will be created to get a good performance.  You will see that this model did perform any better than random chance, which an accuracy score of roughly 85%.

### Metrics

My aim for this model is that it classifies images as accurately as possible.  There is no benefit towards seeing less false negatives over false positives and visa versa since both scenarios result in a misclassification.  For this reason, I choose to optimize for accuracy.  

### Success Criteria 

For these models, I aim to create a model that performs at, at least 85% accuracy and that also shows little-to-no overfitting.  

## Model Evaluations

The final model declared in this notebook performs quite well and classifies images with an 85% test accuracy.  However, I believe the performance is actually better than this given some of the class similarities.  It is often difficult, for even a human, to distinguish between some of the `glacier` and `mountain` images and also between the `street` and `building` images.  The majority of misclassifications are usually mountains being classified as glaciers (and visa versa) and streets being classified as buildings (and visa versa).  For the goals of this project, which is to organize user's photos, I think these misclassifications would actually still achieve our goal of image organization.

Due to time constraints and the extended time it took to run later models, I did not have the chance to apply transfer learning as planned.  Future iterations will definitely include this.  Due to overfitting still being present in some models, I will also experiment with other regularization techniques such as L1 and L2 regularization. 

As you will see in my [Nature Scenery Prediction notebook], my model was a convolutional neural network and achieved a training accuracy score of 0.8888 and a test accuracy of 0.8500.   
