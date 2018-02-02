# **Traffic Sign Recognition** 
## **Build a Traffic Sign Recognition Project**

[//]: # (Image References)

[image1]: ./pics/data1.png "Visualization"
[image2]: ./pics/originNew.png "Testimages"
[image3]: ./pics/predictNew.png "predictResults"
[image4]: ./pics/softmax.png "predictResults"
### **1. Data size**
the data from  [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset).
Download from this [site](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/5898cd6f_traffic-signs-data/traffic-signs-data.zip), which had the image to 32×32.
`data info:`
* Number of training examples = 34799
* Number of validation examples = 4410
* Number of testing examples = 12630
* Image data shape = (32, 32, 3)
* Number of classes = 43
`some data and labels:`
![alt text][image1]

### **2. Preprocess**
only shuttle the data just like: *X_train, y_train = shuffle(X_train, y_train)*

### **3. Model Architecture**
the original network from [LeNet-Lab](https://github.com/udacity/CarND-LeNet-Lab)
Implement the [LeNet-5](http://yann.lecun.com/exdb/lenet/) neural network architecture.
 ### 3.1. Input
The LeNet architecture accepts a 32x32xC image as input, where C is the number of color channels. if are grayscale, C is 1 in this case. The channles in those image is 3(RGB)

#### 3.2. original LeNet Architecture
**Layer 1: Convolutional.** The output shape should be 28x28x6.
**Activation.** Your choice of activation function.
**Pooling.** The output shape should be 14x14x6.

**Layer 2: Convolutional.** The output shape should be 10x10x16.
**Activation.** Your choice of activation function.
**Pooling.** The output shape should be 5x5x16.

**Flatten.** Flatten the output shape of the final pooling layer such that it's 1D instead of 3D. The easiest way to do is by using `tf.contrib.layers.flatten`, which is already imported for you.

**Layer 3: Fully Connected.** This should have 120 outputs.
**Activation.** Your choice of activation function.

**Layer 4: Fully Connected.** This should have 84 outputs.
**Activation.** Your choice of activation function.

**Layer 5: Fully Connected (Logits).** This should have 10 outputs.

#### 3.3  Used network:
**Layer 1: Convolutional.** The output shape should be 30x30x6.
**Activation.** Your choice of activation function.

**Layer 2: Convolutional.** The output shape should be 28x28x6.
**Activation.** Your choice of activation function.
**Pooling.** The output shape should be 10x10x6.

**Layer 3: Convolutional.** The output shape should be 10x10x16.
**Activation.** Your choice of activation function.
**Pooling.** The output shape should be 5x5x16.

**Flatten.** 

**Layer 4: Fully Connected.** This should have 120 outputs.
**Activation.** Your choice of activation function.
**dropout.**
**Layer 5: Fully Connected.** This should have 84 outputs.
**Activation.** Your choice of activation function.

**Layer 6: Fully Connected (Logits).** This should have 43 outputs.
Final model just like this: 
| Layer         	|     Description	        		| 
|:---------------------:|:---------------------------------------------:| 
| Input         	| 32x32x3 RGB image   				| 
| Convolution 3x3     	| outputs 30x30x6 				|
| RELU			| tf.nn.relu					|
| Convolution 3x3     	|  outputs 28x28x6 				|
| RELU			| tf.nn.relu					|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6  		|
| Convolution 5x5x16    | outputs 10x10x16.      			|
| RELU			| tf.nn.relu					|
| Max pooling	      	| 2x2 stride,  outputs 5x5x16  		    	|
| Flatten		| 1600.        					|
| RELU			| tf.nn.relu					|
| Flatten		| 120.        					|
| RELU			| tf.nn.relu					|
| Flatten		| 84.        					|
| RELU			| tf.nn.relu					|
| Dropout		| 0.7						|
| Flatten		| 43.        					|

#### 3.3  Output
Return the result of the 2nd fully connected layer.

### **4. Results in test dataset and new images**
#### 4.1  Results in test dataset
Test Accuracy = 0.932
Validation Accuracy = 0.933
Train Accuracy = 0.992
more thing can read in report.html.
#### 4.2  Results in new images
the origin data:
![alt text][image2]
the lables: test_labels = [35,38,37,14,13]
the predict results: [35 38 37  1 13]
![alt text][image3]
| Image			|     Prediction	        		| 
|:---------------------:|:---------------------------------------------:| 
| Ahead only      	| Ahead only   					| 
| Keep right     	| Keep right 					|
| Go straight or left	| Go straight or left				|
| Stop	      	    	| Speed limit (20km/h)			 	|
| Yield         	| Yield       					|
the Output Top 5 Softmax Probabilities For Each Image:
![alt text][image4]



