# Detecting Brain Tumor Biomarkers with Deep Learning

----
Project Description
----

This repository is about using deep learning to detect a tumor biomarker in the brain.
This is repo is for a kaggle competition: https://www.kaggle.com/c/rsna-miccai-brain-tumor-radiogenomic-classification

----
Importance
----

"Currently, genetic analysis of cancer requires surgery to extract a tissue sample. Then it can take several weeks to determine the genetic characterization of the tumor. Depending upon the results and type of initial therapy chosen, a subsequent surgery may be necessary. If an accurate method to predict the genetics of the cancer through imaging (i.e., radiogenomics) alone could be developed, this would potentially minimize the number of surgeries and refine the type of therapy required." From: https://www.kaggle.com/c/rsna-miccai-brain-tumor-radiogenomic-classification


----
Preprocessing
----

In the dataset, there are MRI images with different modalities, orientations and slice counts. To be able to put these images through the CNN model, we preprocessed the dicom files to get image modalities and each image's respective orientation. 

#### For 2D Modeling:

All T1w axial images were resized to one-channel (256,256) shape to put through the model. We chose to use only the middle slice which presumably would be of the highest quality image for prediction.

#### For 3D Modeling:

All T1w axial images were resized to one-channel (50,256,256) shape to put through the model. For images with less than or more than 50 slices, each array was either padded or cropped symmetrically.


----
Modeling
----

#### 2D Modeling:

For 2D Modeling, a pretrained Alexnet model was used to serve as a baseline. Max accuracy reached after training is 58% on the training set regardless of whether we trained for 10 epochs or 100 epochs.

#### 3D Modeling:

For 3D Modeling, simplest EfficientNet model(EfficientNet-B0) was used to come up with class probabilites. As we did not have too much time and have access to powerful GPUs, the model was trained for only 10 epochs on a Kaggle GPU. Total training time was around 1.5 hours. Max accuracy reached after training is 54% on the training set.

----
Outcome
----

#### What went wrong?

- 3D model didn't perform as good as planned.
- Training took longer than expected.
- There were some issues with the code versioning on kaggle's online notebooks.

#### What went right?

- The Alexnet model was fast to train and gave better accuracy with the same number of epochs as the 3D model.
- We were able to extract all the relevant metadata from the dicom files.
- We learned about the different ways participant brain data is processed.

----
Next Steps
----

- There are many more combinations to analyze for data preprocessing.
- Finding a pretrained 3D model, preferrably on medical imaging data.
- Training more powerful models for longer.
- Finding more powerful machines.

----
About Us
----
Berkay Canogullari and Victor Palacios are receiving a Master's Degree in Data Science at the University of San Francisco.
Additionally, Both Victor and Berkay are currently working as Data Scientists specializing in Neuroscience-related topics.
