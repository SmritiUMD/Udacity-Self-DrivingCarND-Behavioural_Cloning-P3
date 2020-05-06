# **Behavioral Cloning** 


---

**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report

---
### Files Submitted & Code Quality

#### 1. My project includes the following files:
* model.py containing the script to create and train the model
* drive.py for driving the car in autonomous mode
* model.h7 is final, model.h5 and model.h6 are test models containing a trained convolution neural network 
* writeup_report.md 

#### 2. Submission includes functional code
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h7
```

#### 3. Submission code is usable and readable

The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

### Model Architecture and Training Strategy

#### 1. An appropriate model architecture has been employed

My model consists of a convolution neural network with 3x3 filter sizes and depths between 32 and 128

The model includes RELU layers to introduce nonlinearity , and the data is normalized in the model using a Keras lambda layer (code line 156)

#### 2. Attempts to reduce overfitting in the model


The model was trained and validated on different data sets to ensure that the model was not overfitting . The model was tested by running it through the simulator and ensuring that the vehicle could stay on the track.

#### 3. Model parameter tuning

The model used an adam optimizer, so the learning rate was not tuned manually .

#### 4. Appropriate training data

Training data was chosen to keep the vehicle driving on the road.  I kept on changing my driving pattern.At first attempt, I trained my model by keeping the vehicle in center of the lane most of the time which resulted in vehicle going off the bridge and breaking lanes where the yellow boundary lines are not available. Then, I trained my model on about 4-5 laps with a combination of patterns like keeping vehicle in center of the lane, steering from left, steering from right, moving slowly on sharp turns in different ways like direct turn, going straight and turning, etc. This gave me suitable results. The vehicle is now able to move effortlessly on sharp turns.

For details about how I created the training data, see the next section. 

### Model Architecture and Training Strategy

#### 1. Solution Design Approach


In order to gauge how well the model was working, I split my image and steering angle data into a training and validation set. I found that my first model had a low mean squared error on the training set but a high mean squared error on the validation set. This implied that the model was overfitting. 

To combat the overfitting, I modified the model so that I avoided mantaining same pattern while driving like I avoided keeping vehicle in the center on the lane all the time, otherwise the model would have memorized it. Instead, I keep on changing my behaviour while driving.

The final step was to run the simulator to see how well the car was driving around track one. There were a few spots where the vehicle fell off the track like sharp turn on the bridge and when the boundary side lane line were not visible. To improve the driving behavior in these cases, I changed my driving pattern during training and trained it on 4-5 laps to gather enough data points.

At the end of the process, the vehicle is able to drive autonomously around the track without leaving the road.

#### 2. Final Model Architecture

The final model architecture  consisted of a convolution neural network with the 5 covolutional layers, 4 fully connected layers, and 1 drop out layer.(lines 153-201)

#### 3. Creation of the Training Set & Training Process

To capture good driving behavior, I first recorded two laps on track one using center lane driving. Here is an example image of center lane driving.I then recorded the vehicle recovering from the left side and right sides of the road back to center so that the vehicle would learn to take turns on sharp turns. On the sharp turns I recorded by moving vehicle slowly with different maneuvers each time like direct turn, going straight and turning, etc. This gave me suitable results

I trained on 5 laps to get enough data points.

After the collection process, I then preprocessed this data bynormalizing it with mean around zero and a little standard deviation. I also trimmed the images to keep only road in the frame and eliminate extra features like sky, trees, etc.


I finally randomly shuffled the data set.

I used this training data for training the model. The validation set helped determine if the model was over or under fitting. The ideal number of epochs was 5 for me. I used an adam optimizer so that manually training the learning rate wasn't necessary.
