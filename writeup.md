# Traffic Sign Classifier Writeup
---

[//]: # (Image References)

[image1]: ./examples/chart.png "Visualization"
[image2]: ./examples/Original.png "Original Image"
[image3]: ./examples/Grayscale.png "Grayscale Image"
[image4]: ./examples/Gaussian_Gray.png "Gaussian Blur"
[image5]: ./example_pics/do_not_enter.jpg "No Entry"
[image6]: ./example_pics/forty.jpg "Speed limit (30km/h)"
[image7]: ./example_pics/left.jpg "Keep left"
[image8]: ./example_pics/right.jpg "Keep right"
[image9]: ./example_pics/yield.jpg "General caution"

### 1. Calculate summary statistic of the traffic sign data set.

  - The size of the training set is 34,799
  - The size of the validation set is 4,410
  - The size of the test set is 12,630
  - The shape of a traffic sign image is 32x32x3
  - The number of unqiue classes/labels in the data set is 42
    
### 2. Visualization of the data set.

![alt text][image1]

### 3. Design and Test a Model Architecture

1. First i decided to convert the image to grayscale because I wanted to change the shape of traffic sign image to 32x32x1. After grayscaling the image, I normalized the image to help with the poor contrast. After running the model with this image, I experimented processing the grayscale image through Gaussian Blur and normalized it afterwards. The result resulted in a improvment on the outcome. 

Below is an example of the original image, image with grayscale, and grayscale image with Gaussian Blur.

![alt text][image4]

### 4. Model Architecture


| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 Image   								| 
| Convolution  			| 1x1 stride, valid padding, outputs 28x28x6 	|
| RELU					|												|
| Avg pooling		 	| 2x2 stride,  outputs 14x14x6	 				|
| Convolution 			| 1x1 stride, valid padding, outputs 10x10x16 	|
| RELU					|												|
| Avg pooling		 	| 2x2 stride,  outputs 5x5x16	 				|
| Flatten			 	| outputs 400					 				|
| Fully connected		| outouts 200									|
| RELU					|												|
| Dropout				|												|
| Fully connected		| outouts 100									|
| RELU					|												|
| Dropout				|												|
| Fully connected		| outouts 43									|
|						|												|
|						|												|
 
 ### 5. How did you train your model
 
 Training the model was mostly tweeking the epoch, batch size and learning rate to see if there was any improvement from the original training model from the LeNet lab. I found out that instead of using Max pooling and using the Average pooling there was an improvement on the result. Also I added the dropout in the model which helped my model from overfitting. So after playing and tweeking the model from the LeNet lab, I decided to keep the learning rate of 0.003, epoch of 15, and the batch size of 150.
 
 #### Results
 
      - Validation set accuracy of 0.951
      - Test set accuracy of 0.937
 
### 6. Testing Model on New Images

German Traffic signs found on the web.
 
 ![alt text][image5] ![alt text][image6] ![alt text][image7] ![alt text][image8] ![alt text][image9]
 
 #### Results of the Prediction
 
| Image						|Prediction										| 
|:-------------------------:|:---------------------------------------------:| 
| No Entry					| No Entry   									| 
| Speed limit (30km/h)		| Priority Road 								|
| Keep left					| Keep Left										|
| Keep right	      		| Keep Right					 				|
| General caution			| General Caution								|
 
 #### Image # 1
 
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .346					| No Enrty   									| 
| .157					| Yield 										|
| .109					| Stop											|
| .063					| Turn Left Ahead				 				|
| .016					| No passing for vehicles over 3.5 metric tons	|
 
#### Image # 2
 
 | Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .0147					| Priority road									| 
| .0143					| Stop 											|
| .0131					| Keep RIght									|
| .0090					| Turn Left Ahead				 				|
| .0013					| No Passing		 							|
 
#### Image # 3
 
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .336         			| Keep Left										| 
| .076     				| Speed Limit (70km/h)							|
| .038					| Yield											|
| .034	      			| Road Work						 				|
| .030				    | Go Straight or Left 							|

#### Image # 4
 
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .444         			| Keep Right									| 
| .127     				| Yield 										|
| .043					| Turn Left Ahead								|
| .039	      			| Bumpy Road					 				|
| -0.027				| Go Sraight or Right							|

#### Image # 5
 
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .173         			| General Caution								| 
| .132     				| Traffic Signals								|
| .057					| Pedestrians									|
| .031	      			| Right of the Way at the next intersection		|
| -0.013				| Go Straight or Left 							|
