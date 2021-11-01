#  Topic: Drowsiness Detection



### Subject: AIP391 - Class AI1502
### Instructor guide: 
Teacher Lê Đình Huynh
### Student perform:
Nguyễn Khánh Quân - HE150948
Nguyễn Hoàng Minh - HA150125

### The project is done Windows 10 Pro with tensorflow vesion from 1.8 onwards

This proposed temporal model uses blink features to detect both early and deep drowsiness with an intermediate regression step, where drowsiness is estimated with a score from 0 to 10. 

## Instruction to Run the Code:
*THESE CODES WERE APPLIED ON THE UTA-RLDD DATASET*

*You can refer to the comments inside each .py file for more detailed information*

### 0- Make sure all .py files are downloaded then install all the required packages. You can refer to the following link for a short instruction on installing some of the required packages like dlib:
https://www.pyimagesearch.com/2017/03/27/how-to-install-dlib/

Or for the conda environment you can use the following command lines:

~$ conda install -c anaconda tensorflow-gpu

~$ conda install -c anaconda cmake

~$ conda install -c conda-forge gtk3

~$ conda install -c anaconda libboost

~$ conda install -c menpo wget

~$ wget https://bootstrap.pypa.io/get-pip.py --no-check-certificate

~$ conda install -c conda-forge dlib

~$ conda install -c conda-forge scikit-image

~$ pip install imutils

~$ conda install scikit-learn

~$ conda install -c conda-forge opencv

	
### 1-Run file Blink_Video.py:

  This file is fed by the input video(the directory should be given to the path variable). Then, it detects the blinks and outputs four features of all blinks in a text file.
  
  ("Trained_SVM_C=1000_gamma=0.1_for 7kNegSample.sav" is used for blink detection.)
  
  *Use the link below to download "shape_predictor_68_face_landmarks.dat"
  
  https://drive.google.com/open?id=1nrfc-_pdIxNn2yO1_e7CxTyJQIk3A-vX
  
  "shape_predictor_68_face_landmarks.dat" is the pre-trained facial landmark detector inside the dlib library.

### 2-Run file Preprocessing.py

  This file gets three text files (blink features in three drowsiness levels) as the main input and preprocesses them for the subsequent steps. The outputs are .npy files.
  
  For convenience, these .npy files ({Blinks, BlinksTest, Labels, LabelsTest}_30_FoldX.npy) are provided for each X as the test fold used for five fold cross validation. For example Blinks_30_Fold4.npy is the training set consisted of all the folds except fold 4, and  BlinksTest_30_Fold4.npy is the data from fold 4. If decided to apply this method to a different dataset, then the hard coded "start_indices" array in Training.py should be adjusted accordingly. More info about "start_indices is mentioned in the Training.py". Finally, to clarify, these .npy files are generated from step 1 and 2 on the UTA-RLDD dataset so one might decide to generate their own   .npy files to train. 

### 3-Run file Training.py:

  This code is used to train based on the .npy files generated in step 2. The model details and hyperparameters are all set here. This code is also used for testing. Here, one fold from the dataset (UTA-RLDD in this case) is picked as the test fold and the other four are used for training. The output is the training and test results and accuracies based on the pre-defined metrics in the paper.
 
 
  For convenience, five pre-trained models are provided, where each model used one of the folds as the test set in a five fold cross validation.
  
  These three files are pre-trained models for the training session of fold X, where fold X had been used as the test fold:
  
    my_modelX.data-00000-of-00001
    
    my_modelX.index
    
    my_modelX.meta
  

NOTE: References used for each code are mentioned on top of each code.

#### Reference group source:
The team's project is based on an article by Reza Ghoddoosian on building a model for early sleepiness detection in vehicles with just a regular camera on a phone or a computer camera.
Learn more at:
https://arxiv.org/abs/1904.07312

#### Link UTA-RLDD dataset:

https://sites.google.com/view/utarldd/home
# AIP-Project
