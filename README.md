# SDCND_3rdProject_BehavioralCloning
Navigating a Car in a Simulator

The goals / steps of this project are the following: (to train a deep neural network to drive a car in a simulator as a human would do.)

* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road

I have used the codes present in the the sdcnd and referred the open forum portals.

The project repository includes,
1. model.py (how the model is created and trained)
2. model.h5 (trained convolution neural network)
3. drive.py (driving the car in autonomous mode in the simulator)
4. video.py (To create the video recording when in autonomous mode)
5. AD_RecordVideo.mp4 (Recorded video in autonomous mode)
6. model_JupyterNotebook.ipynb (To see the printed output, how the model is created and trained)

### The code is functional and reusable
### Model Architecture and Training Strategy
#### 1. I have used the nvidia self driving car mpdel(https://devblogs.nvidia.com/parallelforall/deep-learning-self-driving-cars/), 
and the car trained to drive the first track after 3 training epochs 
The model summary is described in next section.
#### 2. attempt to reduce overfitting of the model
I splitted my sample data into training and validation data.  80% as training + 20% as validation.

#### 3. Have the model parameters been tuned appropriately?
The model used an Adam optimizer, so the learning rate is not tuned manually 

#### 4. Is the training data chosen appropriately?
Training data is collected with following the steps given in classroom, keep the vehicle driving on the road in the first track.
The simulator provides three different images: center, left and right cameras. Each image was used to train the model.

### Architecture and Training Documentation
1 Is the solution design documented?
yes, followed the same steps given in the classroom session. 'Lambda' layer was introduced to normalize the input images to zero means. This step allows the car to move a bit further, but it didn't get to the first turn. Another 'Cropping' layer was introduced, and the first turn was almost there, but not quite.
add a new layer at the end to have a single output as it was required. This time the car did its first complete track, but there was a place in the track where it passes over the "dashed" line. More data was needed. Augmented the data by adding the same image flipped with a negative angle. In addition to that, the left and right camera images where introduced with a correction factor on the angle to help the car go back to the lane. 

2. Is the model architecture documented?
____________________________________________________________________________________________________
Layer (type)                     Output Shape          Param #     Connected to                     
====================================================================================================
lambda_1 (Lambda)                (None, 160, 320, 3)   0           lambda_input_2[0][0]             
____________________________________________________________________________________________________
cropping2d_1 (Cropping2D)        (None, 90, 320, 3)    0           lambda_1[0][0]                   
____________________________________________________________________________________________________
convolution2d_1 (Convolution2D)  (None, 43, 158, 24)   1824        cropping2d_1[0][0]               
____________________________________________________________________________________________________
convolution2d_2 (Convolution2D)  (None, 20, 77, 36)    21636       convolution2d_1[0][0]            
____________________________________________________________________________________________________
convolution2d_3 (Convolution2D)  (None, 8, 37, 48)     43248       convolution2d_2[0][0]            
____________________________________________________________________________________________________
convolution2d_4 (Convolution2D)  (None, 6, 35, 64)     27712       convolution2d_3[0][0]            
____________________________________________________________________________________________________
convolution2d_5 (Convolution2D)  (None, 4, 33, 64)     36928       convolution2d_4[0][0]            
____________________________________________________________________________________________________
flatten_1 (Flatten)              (None, 8448)          0           convolution2d_5[0][0]            
____________________________________________________________________________________________________
dense_1 (Dense)                  (None, 100)           844900      flatten_1[0][0]                  
____________________________________________________________________________________________________
dense_2 (Dense)                  (None, 50)            5050        dense_1[0][0]                    
____________________________________________________________________________________________________
dense_3 (Dense)                  (None, 10)            510         dense_2[0][0]                    
____________________________________________________________________________________________________
dense_4 (Dense)                  (None, 1)             11          dense_3[0][0]                    
====================================================================================================


3. Is the creation of the training dataset and training process documented?
I collected the data in entering the training mode in simulator in first track. All these data is used for training with three epochs.
Total Images: 24108
Train samples: 19286
Validation samples: 4822

After this step the car drove in centre of the track all the time - 'AD_RecordVideo.mp4'
