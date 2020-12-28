# Steel-Defect-Detection-using-Object-Segmentation

![CV](https://img.shields.io/badge/CV-Object Segmentation-blue.svg) 

![logo](Snips/Severstal_logo.png)

## Business Objectives :

Steel is one of the most important building materials of modern times. Steel buildings are resistant to natural and man-made wear which has made the material ubiquitous around the world. 

Severstal is leading the charge in efficient steel mining and production. They believe the future of metallurgy requires development across the economic, ecological, and social aspects of the industry—and they take corporate responsibility seriously. The company recently created the country’s largest industrial data lake, with petabytes of data that were previously discarded. Severstal is now looking to machine learning to improve automation, increase efficiency, and maintain high quality in their production.

The production process of flat sheet steel is especially delicate. From heating and rolling, to drying and cutting, several machines touch flat steel by the time it’s ready to ship. 

In this project the objective is to predict the location and type of defects found in steel manufacturing. Given a image, the task is to classify the defect and locate the segmentation of the defect.

## Data Collection :

The data was obtained from Kaggle. 

Link: https://www.kaggle.com/c/severstal-steel-defect-detection/data

The data file consists of:
  - DataTrain_images.Zip: Zip file containing all train images (12568 unique)
  - Test_images.zip: Zip file containing all test images (1801 unique)
  - train.csv: containing Imageid and Encoded Pixels columns
  - submission.csv: test csv file containing Imageid and Encoded Pixels columns

Each image is of size 1600 x 256 and may have no defects, a defect of a single class, or defects of multiple classes (ClassId = [1, 2, 3, 4]).

There are two tasks associated with this problem
  1. Classification of image into 4 defected classes (ClassId = [1, 2, 3, 4]).
  2. Predict the location of defects found (segmentation)

## Modelling :

The analysis and model creation can be found in the .ipynb file. 

## Result :

Some of the test images are as follows:

![test](Snips/5.jpg)
![test](Snips/4.jpg)
![test](Snips/3.jpg)
![test](Snips/2.jpg)
![test](Snips/2.jpg)


## Conclusion :

As this problem dealt with binary classification, multi label classification and segmentation, the following approach was used to generate the results:
  - First, getting the image from the data pipeline and feeding it into the binary classifier to filter out the defected and undefected images apart
  - Then, filter out the undefected images and proceed with only defected images detected by the binary classifier
  - Then, put the defected images inside the multi label classifier detect the Defect Class 
  - Then, each defect will go to their corresponding individually trained model per defect and to get the mask in the size (256, 800, 1) which will be resized to the original image size of (256, 1600, 1) which can be correctly converted to run length encoding of the mask

# Further scope :

  - The results are good using the current approches, but there is still some scope to improve the model using more newer SOTA models
