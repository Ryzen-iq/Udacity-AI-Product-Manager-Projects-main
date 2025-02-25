# Udacity-AI-Product-Manager-Projects
This repository contains Udacity AI Product Manager Nanodegree Tasks and Assignments to prepare individuals to advocate how to build and validate AI products
that serve customers and meet business needs from the scratch to deployment.
This challenge is the Phase II of Scholarship given by Bertelsmann via Udacity. In this phase, 1k scholars out of `15,000` participants worldwide were selected to learn further in one of fully-funded courses of Udacity's AI Product Manager Nanodegree.

It has two sections, which are the core concept and advance concept. The core concept is about Introduction to AI, Descriptive Statistic, Project Evaluation. The advance concept has three industry level projects. This type of course has a lot of quizzes, practical learnings to help us to have deeper understanding about the concept and practice by solving problems from different point of view.

This Repository consists of all projects that are completed as part of AI Product Manager Nanodegree Program powered by Udacity and Bertelsmann.


For now, see my Nanodegree files

Contact me :

`ON LINKEDIN:`[Site](https://www.linkedin.com/in/trustayeni/)

and

`Email:`[Google mail](trust.ayeniolamilekan@gmail.com)


## Build a Model with Google AutoML

>- Overview
In this project, we need to build a labeled dataset that distinguishes between healthy and pneumonia x-ray images.This dataset would eventually be used to build a product that helps doctors quickly identify cases of pneumonia in children.we are going to take the next step and build the classification model that would serve as the backbone of this product.For this task,we will use Google AutoML,an automated machine learning tool that will allow us to build the model and host it in the cloud. In order to appreciate how training data impact models,we will build models with 4 variants of the dataset.The goals of this product are

- Help flag serious cases,
- Quickly identify healthy cases,
- And, generally, act as a diagnostic aid for doctors.

>- The Four Parts of the Project
We will train four different models using four variants of the pneumonia dataset.The dataset contains childrens' chest x-ray images, and that they are classified into two classes, "normal" and "pneumonia". The following cases describe the steps we must take to create each model.

- Case 1: Create a binary classifier to detect pneumonia using chest x-rays
We'll start by training a model simply using 100 images from the “normal” class and 100 images from the “pneumonia” class.We are asked to evaluate the following:

Train/test split: How much data is used for training and how much is used for testing?
Confusion matrix: What do each of the cells in the confusion matrix describe?
Precision & recall: What do these measure and how are they calculated?

- Case 2: Create an unbalanced binary classifier
Next, use 100 images from the “normal” class, and add 200 more "pneumonia" class images. At this moment, the total count of images must be:

“normal” class = 100 "pneumonia" class = 300 The model will be trained on very unbalanced classes; this will show what happens when the number of images in different classes is very different. We are asked to evaluate:

Confusion matrix: What does the confusion matrix tell you about unbalanced data?
Precision & recall: How are precision and recall affected?
Unbalanced classes: How do unbalanced classes impact a machine learning model?

- Case 3: Create a binary classifier with dirty data
In this iteration, start with the original dataset of 100 "normal" and 100 "pneumonia" images. Then switch the labels of 30 images in each class. After we've done this, 30% of the data are mislabeled. We are asked to evaluate:

Confusion matrix: How is the confusion matrix affected?
Precision & recall: How are precision and recall affected?
Dirty data: How do dirty data impact the model?

- Case 4: Create a three-class model with the classes “normal”, “bacterial pneumonia”, and “viral pneumonia”
For the final model, note that the "pneumonia" images actually have two different classes: "bacterial" pneumonia and "viral" pneumonia. These labels are indicated in the image filenames. For this model, add 100 "normal" images, 100 "bacterial pneumonia" images, and 100 "viral pneumonia" images (for a total of 3 classes). We are asked to evaluate:

Confusion matrix: What does the 3-class confusion matrix look like?
Precision & recall: What are the model's precision and recall? How are these measures calculated?
More data: Can we continue to add data to each class (while keeping the data balanced) and get the model to 85% precision and recall? How many data did you end up using?
Google Cloud AutoML Vision
The following steps will guide us through the process of creating and training a model on Google Cloud's AutoML Vision platform.

>- Step 1
Download Kaggle Chest X-Ray Images (Pneumonia) Dataset from the below link,
[here](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia#chest_xray.zip.)


>- Step 2
Go to Google AutoML: [here](https://cloud.google.com/automl/)


>- Step 3
Click “TRY AUTOML” and select “AutoML Vision”.


>- Step 4
Sign in to Google Developer or create an account.


>- Step 5
After logging in, head to the AutoML Vision Console: [here](https://console.cloud.google.com/vision) and Accept the terms of service.


>- Step 6
Next create a project with any title.


>- Step 7
Once on the dashboard click “Get Started” on AutoML Image Classification.


>- Step 8
Accept all the screens then we will reach the last page where we have to set up billing and Vision API.


>- Step 9
When we go to billing we should see an option to activate free `$300` credit at the top of the screen. Click `ACTIVATE`.


>- Step 10
We now provide our Email ID and click on next.Once the phone number is verified, we will be redirecting to the last page for activating the credit. Then select `_Individual_` account type and input all necessary info including card. Google does not charge this card unless you manually upgrade to a paid account.


>- Step 11
Once we have completed the billing we can go back to the project set up page and click `SET UP NOW` to enable the vision API. This will automatically set up the API and should redirect us to select the Google Cloud Project.In the dropdown we should see the project that we created. Select the project and continue.


>- Step 12
Next, we should see the Datasets page. Click `Create` at the top of the page.


>- Step 13
Select `Single-Label Classification`.


>- Step 14
Create your dataset.

Give the dataset a name and create bucket by clicking on `Browse` under Upload data option.
Open the folder of Chest Xrays we downloaded from Kaggle and go into the train folder.
In a separate folder create a directory with the following structure:
(Main folder) Case 1/
normal/
pneumonia/
Then copy between 100-300 images of each type of each classification from the original train/ folder (normal, pneumonia) into the appropriate new folder. The exact number of images in each folder will depend on which of the four parts of the project you are solving,Once you have your images in the new folders then zip the whole Case 1/ folder to create Case 1.zip.


>- Step 15
Now back in the AutoML Console Dataset go ahead and upload the zip file with all the images. Again, make sure we zipped the top-level folder that contains two folders: normal/ and pneumonia/ with the associated sets of 100-300 images in each folder (the exact number of images will depend on which of the four parts of the project we are solving). This will allow AutoML to automatically detect the correct ground truth label for each image by looking at the name of the folder in which it is contained. Once the zip file is attached go ahead and `CREATE DATASET`. For our current labeling scheme, there is no need to select the button to "_Enable multi-label classification_" (this allows you to apply multiple labels to a single image). This step make take a few minutes to upload all the images and set up the dataset.


>- Step 16
Once the data is ready we should see a screen with all the images we added as well as a label of `normal` or `pneumonia` under each image. These are the images and ground truth labels that will be used to train/test/validate your pneumonia detector model.


>- Step 17
Next click on the `TRAIN` tab and here we will see the distribution of images as well as the splits for training, validation, and test images.


>- Step 18
Click `START TRAINING` to begin training your pneumonia classification model. In the options keep all the defaults (Cloud-hosted, 8 node hour) and then start the training.


>- Step 19
Now the model is in the training phase.This will take some time. Once the model training is done we will be notified via email and we can see the below results.


>- Step 20
Once the training is complete we can click on the `EVALUATE` tab and we will see various metrics about the model such as precision, recall, and a confusion matrix. Try to understand what each of these metrics means and how they are calculated.


>- Step 21
Optional: Next click on the `TEST&USE` tab and this is where we can test the model on new data that the model has never seen. If we click `UPLOAD IMAGES` and select an image from the Kaggle dataset that we did NOT use in the training set of images and watch the model predict whether or not the patient in the x-ray has pneumonia or not.Try to find images that produce both correct and wrong predictions.


>- Step 22
That's it! we've built our first AI model! Now that we know how to upload data and train the model, follow the steps above for 3 additional variations on the dataset, for a total of 4 models.Recommend creating new folders, new zip files, and new datasets in AutoML so that we can keep track of which iteration we're on and retain the results of each trained model for reference:

- Clean/Unbalanced: Create a model using 100 "normal" images and 300 "pneumonia" images.

- Dirty/Balanced: Create a model with 100 "normal" images and 100 "pneumonia" images, but deliberately create a "dirty" dataset by putting 30 "normal" images in the pneumonia folder and 30 "pneumonia" images in the normal folder.

- 3-Class: Note that the filenames of images in the "pneumonia" class have 2 standards; for example: person75_bacteria_366.jpeg and person80_virus_150.jpeg. The inclusion of the word "bacteria" indicates that this was a case of bacterial pneumonia, and the word "virus" means this was a case of viral pneumonia. Go back and create a dataset with 3 
classes: "normal", "bacterial pneumonia" and "viral pneumonia".

Once you have completed the project, don't forget to disable the Google Cloud Platform billing for this project.

The various screenshots for Case 2(Unbalanced data),Case 3(Dirty data),Case 4(3-Class data) are available in docx 



## Verify my Certificate
[Link to verify](https://confirm.udacity.com/USDVQUFE)
