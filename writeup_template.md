# **Traffic Sign Recognition** 

## Writeup

### You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/visualization.jpg "Visualization"
[image2]: ./examples/grayscale.jpg "Grayscaling"
[image3]: ./examples/random_noise.jpg "Random Noise"
[image4]: ./examples/placeholder.png "Traffic Sign 1"
[image5]: ./examples/placeholder.png "Traffic Sign 2"
[image6]: ./examples/placeholder.png "Traffic Sign 3"
[image7]: ./examples/placeholder.png "Traffic Sign 4"
[image8]: ./examples/placeholder.png "Traffic Sign 5"

## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/481/view) individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

You're reading it! and here is a link to my [project code](https://github.com/udacity/CarND-Traffic-Sign-Classifier-Project/blob/master/Traffic_Sign_Classifier.ipynb)

### Data Set Summary & Exploration

#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34799
* The size of the validation set is 4410
* The size of test set is 12630
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43

#### 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data ...

![alt text][image1]

### Design and Test a Model Architecture

#### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)
#Pre-process the Data Sets
1. calculate mean along axis=3 annd gray scale
2. normalize the data set using  (image_sets - image_sets_.mean())/image_sets_.std()



Here is an example of a traffic sign image before and after grayscaling.

![alt text][image2]

As a last step, I normalized the image data because ...

I decided to generate additional data because ... 

To add more data to the the data set, I used the following techniques because ... 

Here is an example of an original image and an augmented image:

![alt text][image3]

The difference between the original data set and the augmented data set is the following ... 


#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 grayscale image   							| 
| Convolution 5x5     	| 1x1 stride, same padding, outputs 28x28x6 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6	
| Input                	| 14x14x6	grayscale image  			|
| Convolution 5x5       | 1x1 stride, same padding, outputs 10x10x16 	   									|
| RELU	
| Max pooling	      	| 2x2 stride,  outputs 5x5x16					|												|
| Fully connected	| input 400,   output 120    									|
| Dropout		| KEEP_PROBABLITY 0.6     									|
| Fully connected	| input 120,   output 84    									|
| Dropout		| KEEP_PROBABLITY 0.6   |        						|												|
| Fully connected	| input 84,   output 43    					|												|
 


#### 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

To train the model, I used an ....
LEARNING_RATE = 0.001
EPOCHS = 40
BATCH_SIZE = 128
keep_prob = 0.6

#### 4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

My final model results were:
* training set accuracy of 99.8
* validation set accuracy of 96.3 
* test set accuracy of 94.1

If an iterative approach was chosen:
* What was the first architecture that was tried and why was it chosen?
* What were some problems with the initial architecture?
* How was the architecture adjusted and why was it adjusted? Typical adjustments could include choosing a different model architecture, adding or taking away layers (pooling, dropout, convolution, etc), using an activation function or changing the activation function. One common justification for adjusting an architecture would be due to overfitting or underfitting. A high accuracy on the training set but low accuracy on the validation set indicates over fitting; a low accuracy on both sets indicates under fitting.
* Which parameters were tuned? How were they adjusted and why?
* What are some of the important design choices and why were they chosen? For example, why might a convolution layer work well with this problem? How might a dropout layer help with creating a successful model?

If a well known architecture was chosen:
* What architecture was chosen - LeNet Architecture with max pooling and dropout and keep_prob = 0.6
* Why did you believe it would be relevant to the traffic sign application - It increase my model accuracy 
* How does the final model's accuracy on the training, validation and test set provide evidence that the model is working well - training set accuracy of 99.8
* validation set accuracy of 96.3 
* test set accuracy of 94.1

 

### Test a Model on New Images

#### 1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are five German traffic signs that I found on the web:

![Stop Sign ][image4] ![ Yield][image5] ![100 km/h][image6] 
![Bumpy Road][image7] ![Slippery Road][image8] ![100 km/h[image8]

The first image might be difficult to classify because ...

#### 2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Stop Sign      		| Stop sign   									| 
| U-turn     			| U-turn 										|
| Yield					| Yield											|
| 100 km/h	      		| Bumpy Road					 				|
| Slippery Road			| Slippery Road      							|


The model was able to correctly guess 4 of the 5 traffic signs, which gives an accuracy of 80%. This compares favorably to the accuracy on the test set of ...

#### 3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

The code for making predictions on my final model is located in the 11th cell of the Ipython notebook.

For the first image, the model is relatively sure that this is a stop sign (probability of 0.99), and the image does contain a stop sign. The top five soft max probabilities were
   
       
    
    

| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 9.9852908e-01      			| Stop sign   |					|  		
| 1.4658967e-03                         | Yield 									|
| 4.4001440e-06			        | Bumpy Road											|
| 5.6511442e-07	      			| slippery road					 				|
| 4.7913982e-08			        | speed-limit 80km 
| 3.9930526e-08     			| Roundabout mandatory   							|


For the second image ... 

 1.1299407e-31 5.8368983e-35 5.0104765e-36 0.0000000e+00
 0.0000000e+00

| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 00       			| Stop sign   |					|  		
|  00                                     | Yield 									|
| 1.0000000e+00			| Bumpy Road											|
| 00	      			| slippery road					 				|
| 00			        | speed-limit 80km 
| 00    			| Roundabout mandatory   							|


For the third image ... 

| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.3806533e-06        			| Stop sign   |					|  		
|                                       | Yield 									|
|  1.4506855e-08			| Bumpy Road											|
| 9.9999857e-01      			| slippery road					 				|
| 1.4506855e-08		        | speed-limit 80km 
| 1.8953806e-12     			| Roundabout mandatory   							|


For the fourth image ... 


| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 00       			| Stop sign   |					|  		
| 00                                      | Yield 									|
| 00			| Bumpy Road											|
| 1.0000000e+00	      			| slippery road					 				|
| 00			        | speed-limit 80km 
|00     			| Roundabout mandatory   							|



For the fifth image ... 


| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 2.1586115e-02        			| Stop sign   |					|  		
| 9.9301418e-05                                      | Yield 									|
|  1.4658967e-03			| Bumpy Road											|
| 4.4001440e-06	      			| slippery road					 				|
| 9.7795850e-01			        | speed-limit 80km 
| .3120192e-05     			| Roundabout mandatory   							|



### (Optional) Visualizing the Neural Network (See Step 4 of the Ipython notebook for more details)
#### 1. Discuss the visual output of your trained network's feature maps. What characteristics did the neural network use to make classifications?


