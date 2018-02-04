# SDCND_3rdProject_BehavioralCloning

The project repository includes,
1. model.py
2. model.h5
3. drive.py
4. video.py
5. AD_RecordVideo.mp4

### The code is functional and reusable
### Model Architecture and Training Strategy
#### 1. I have used the nvidia self driving car mpdel(https://devblogs.nvidia.com/parallelforall/deep-learning-self-driving-cars/), 
and the car trained to drive the first track after 3 training epochs 

model summary:


#### 2. attempt to reduce overfitting of the model
I splitted my sample data into training and validation data.  80% as training + 20% as validation.

#### 3. Have the model parameters been tuned appropriately?
The model used an Adam optimizer, so the learning rate is not tuned manually 

#### 4. Is the training data chosen appropriately?
Training data is collected with following the steps given in classroom, keep the vehicle driving on the road in the first track.
The simulator provides three different images: center, left and right cameras. Each image was used to train the model.

### Architecture and Training Documentation
1 Is the solution design documented?

2. Is the model architecture documented?

3. Is the creation of the training dataset and training process documented?



