# Omdena_Harrasment_prediction_competion
This project is part of my omdena global competition, here we are given an anonymous crime data collected by safecity consist of Lat &amp; long and incident record, I am creating machine learning to predict the safety of region.

[JupyterNB Viewer Link](https://nbviewer.jupyter.org/github/saurabh241930/Omdena_Harrasment_prediction_competion/tree/master/)

Note: So for identifying safety, for 1st problem statement, I tried different types of method, following are some of the highlights of all the method that I have tried and will try to implement in coming weeks

Since many participants are doing the spatial-temporal way of classifying regions into safe or not safe to avoid overlapping I’m exploring the more unconventional way of classifying, By just using deep learning techniques  & computer vision

 
## Inputs:

So for the inputs(Sattelite image & street image), I used Mapquest(I liked their quality compare to google static images)

<img src="https://i.imgur.com/wttys9v.jpg" border=0>
Objective of model:

Given the lat & long of place, the model should output if its safe or not.


# Approaches :

## 1st(Most naive approach)(Binary CNN classification on the original satellite image)

For the first approach, I trained a Keras CNN Binary classifier based on image 

Unsafe location images > Image collected by lat & long by safecity dataset

safe location images > Image collected by lat & long by safecity hospital & police stations locations dataset

<img src="https://i.imgur.com/IyTWrSq.png" border=0>

Now we can pre-process image for better results we can various pre-processing techniques used for pre-processing satellite image like a watershed, etc, I’ll experiment with but I don't think so it will improve performance.

<img src="https://i.imgur.com/NsMbrcY.png" border=0>

## Feature embedding way


The features that we are dealing with are really granular in nature but similar(present of schools, street roads, building rooftops, etc)

So I think if we could train a model to identify the similarity between images in terms of recurrent features then it will be much easier to identify the safeties of the given input map image.

<img src="https://i.imgur.com/MshhHE1.png" border=0>

<img src="https://i.imgur.com/STop5mp.png" border=0>

## Feature Engineering:

 note that this feature alone won't able to create feature ,so I am planning to use other **numerical & categorical** data

### Features(as of now):


* UnProcessed Satellite image
* Bounding Box locations of buildings for spatial feature extraced my pre-trained **MASK_RCNN**.
* Detecting presence of (**Schools,Police Stations , Companies , Hospitals**) using **OCR** on non-sattelite image.
* Statistical data like location wise**Crime conviction rate,Literacy rate** ,etc. from `data.gov.in`



### Mask RCNN Part
To identifying the buiding positions building , I am planning to use pre-trained **mask-rcnn** model used by Neptuneml on sattelite images


<img src="https://i.imgur.com/R0MF98K.png" border=0>

### OCR part

Identifying the presence of Schools,Police Stations , Companies , Hospitals,etc by eunning on this version of image.
<img src="https://i.imgur.com/tRGHbky.gif" border=0>

So instead of training OCR from scratch I,m planning to OCR service api and use that information

