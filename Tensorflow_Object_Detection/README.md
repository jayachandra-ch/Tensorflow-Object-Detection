# Tensorflow Object Detection API Example With Custom Dataset

##Waste bags Detector 

[TensorFlow's Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection)

-----------------------------------------------------------------------------------------------------------------------------------------
## Steps to be followed for this detector to be working:

### Step 1:

=> Install Tensorflow 1.15.0 version using the below command.
=> To install the CPU-only version of TensorFlow, enter the following command.

     C:\> pip3 install --upgrade tensorflow.

     C:\> conda install tensorflow==1.15	

=> To install the GPU version of TensorFlow, enter the following command.

     C:\> pip3 install --upgrade tensorflow-gpu


		
### Step 2:

=> Object Detection Api will not be installed when we use pip installation of tensorflow. 

=> So clone the Object detection tensorflow gitub repository  by going to this link [TensorFlow's Object Detection API] (https://github.com/tensorflow/models).

=> This should be cloned to the location where Tensorflow is installed. In my laptop it is installed in this location.

   (C:\Users\cvc\anaconda3\envs\TfodAPI\Lib\site-packages\tensorflow).
   
=> So I cloned the  [TensorFlow's Object Detection API] (https://github.com/tensorflow/models) into the above location.


   
### Step 3:

=> Install the following through pip install command.

pip install pillow.

pip install lxml.

pip install jupyter.

pip install matplotlib.

pip install protobuffer.


		
### Step 4:

=> Protobuf Compilation:

The Tensorflow Object Detection API uses Protobufs to configure model and training parameters. Before the framework can be used, the Protobuf libraries must be compiled. This should be done by running the following command from the tensorflow/models/research/ directory:

=> From tensorflow/models/research/  folder in command line   run the below command.

protoc object_detection/protos/*.proto --python_out=.  

=> If you are getting error in running the above then run the above command for individual .proto files one by one in that location as follows:
   protoc object_detection/protos/anchor_generator.proto --python_out=.

   
  
### Step 5:

=>From tensorflow/models/research/  folder in command line   run the below command :

python setup.py install
	 
=>From tensorflow/models/research/slim  folder in command line   run the below command :

python setup.py install.



	 
### Step 6:

=> Testing the Installation.

#From tensorflow/models/research/

=> You can test that you have correctly installed the Tensorflow Object Detection API by running the following command:

python object_detection/builders/model_builder_test.py

=> If everything in the above steps go fine then Tensorflow object detection Api is successfully installed in your machine. 
   Now we will	proceed to create our own Object detection system with our custom data set.

-------------------------------------------------------------------------------------------------------------------------------------------------

## Steps for creating our own object detector with custom data set:

### Custom Dataset creation steps:

=> In this repository I have created the Waste bag detector.

=>Go to the DataSet_Creation_Procedure.md file.
  and create the dataset which could be feed to the Tensorflow object detection Api.

-------------------------------------------------------------------------------------------------------------------------------------------------

	
### Addressing the Limitations of the detector:

=> Since I trained this with less data and for only few hours on a CPU the accuracy will be sometimes less.But if you train with large dataset and with huge GPU power then accuracy will be high.

=> Collect data in different criteria such as change in lighting conditions, view, distance, different background etc.

=> Use data augmentation to generate more data. It is also a form of regularisation.

=> Try different feature extractors (back bone). 

=> Currently Single Shot Detector and Faster RCNN is tested. I It is observed that Faster RCNN is better in terms of accuracy compared to SSD. However, Faster RCNN also struggles as bounding box based annotation introduces noise (Waste bag detection is non rigid object detection). This can be further improved by using Mask RCNN where instances can be annotated using polygons. VGG annotator can used to draw polygons around instances. Further, Mask RCNN achieves high precision compared Faster RCNN.  

=> I believe that the addition of instance segmentation greatly helps to identify objects with very little labeling because this additional mask blocks out extra noise around the photo along with the overall training process.

=> The Mask R-CNN code also uses a Feature Pyramid Network, which can detect the same image on multiple scales. This solves the problem of doing lots of annotations to get good results.

=> Iteratively improve the performance of the detector using hyper parameter tuning. Use different optimisation algorithms such as gradient descent with momentum, Nestrov acceleration, Adagrad, Adadelta etc. Try different initialisation techniques and activation functions etc. Batch size and learning rate can also very important hyperparameters. 

=> Observe the loss curves and early stop the training where the overfitting problem is noticed.

=> Some of the major challenges for the object detectors are scale variance, rotational variance, domain adaptation, object localisation, occlusions and detecting small objects.

=> Take the fined tuned accuracies as the benchmark and train from scratch and then compare the performance.

 







