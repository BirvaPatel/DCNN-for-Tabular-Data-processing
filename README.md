# DCNN-for-Tabular-data
This work showcases our capstone project for the Masters program in Data Science at Lakehead University, Thunder Bay. The project uses the Tabular datasets of different size range which includes Connect4, Covertype, EEG, Letter recognition, Hepmass-OS, Hepmass-NS, Hepmass- AS and HIGGS. The objective of this work is to build a DCNN model That can be used for tabular data. But as we know, DCNN gives excellent performance for an image classification. Therefore we decided to make a system that converts the tabular data into images and later on that images will be pass to the DCNN model for classification. This project work is executed by very few researchers and programers. Among all of them, our designed model gives best performance till the date.<br/> 
# **Datasets:**<br/>
We have experimented on different datasets to check the model’s capacity. Which includes small datasets like Iris to Large datasets such as HIGGS. Distribution of datasets for Training and testing is as follows:<br/><br/>

<img src="https://image.prntscr.com/image/tvbm3mJPQI6kicnsnDfweg.png" width="800" height="600"><br/>
# **Methodology:**<br/>
1. Load the dataset(connect4, covertype,Hepmass-A,O,N,HIGGS).
2. Apply Normalization methods like one hot encoding to get the shape.
3. Split the data into train and test according to requirements.
4. Feature extraction(Our method) to get image data.
5. Concatenate on horizontal axis(now total attribute number is equal to    nearest square number).
6. Convert this attribute values into image pixels(by resizing It to (32,32) and copy 3 times on z axis(32,32,3)).
7. Use DenseNet121 model from the keras for training the model and evaluate it on test data.<br/>

We have used feature extraction method to convert the data into images. This have been achieved by using Simple neural network architecture make feature extraction process faster.<br/>  
### What is Feature extraction and how it is used in our project<br/>
<br/>Feature Extraction means take out the important informationfrom the data that are lesser in volume than original data. We have  features  in  tabular  format  and  the  number  of  features will  not  be  enough  to  convert  them  into  images.  
i.e  It  is  not a  perfect  square  number.  So  we  generate  new  extra  features from original features. In our approach, we use a simple neural network as a FE method. 
What it does is that pass the wholedataset  (m,n)  and  convert  it  to  the  (m,  N)  whereN≤n,  N is a perfect square number. 
So, the hidden layer of the NN is having an r number of nodes (r = n-N). The last layer contains the node that equals the number of classes in the dataset. 
We can extract the feature from that hidden layer and join it with the  original  n  features. <br/>
Now,  there  are  N  total  features  and transfer it to the (p,p) where p is the square root of N.
<br/>To understand this,let’s take the example of the EEG dataset, which has 310 features, and to convert it to the nearestsquare(18*18), we need the remaining 14 more attributes. 
To do that, we can use a dense layer to get new 14 features from the  available  310.  Combine  them  and  use  them  to  train  the model  on  the  image  dataset. 
<br/> Now  that  we  have  310  original features  and  14  new  generated  features,  we  can  concatenatethem  on  the  horizontal  axis. 
Once  we  get  the  combined features,  we  can  start  the  process  of  converting  the  features to image. Therefore, we will have to reshape the dataset from 2D to 3D.
For our example, it would be (m,18,18) for (m,324)in EEG dataset.<br/><br/>

<img src="https://image.prntscr.com/image/URL4iG_cQ5KNeK24SKQUZA.png" width="800" height="600"><br/>
# **How to Use:**<br/>
**Step-1 Get the code** <br/>
Clone the repository or download the source code. <br/>
$ git clone https://github.com/parthvalani/DCNN-for-Tabular-data<br/>
$ cd ./parthvalani<br/>
**Step-2 Download the dataset**<br/>
Download the dataset that you want to use for this model.<br/>
Divide it in train and test. Apply normalization method to get the data in shape.<br/>
**Step- 3  Use our model**<br/>
Now that data is ready, use our model to convert the tabular data into images.<br/>
**Step- 4 Classification**<br/>
Our method gives best performance with using DenseNet121 but if you want to use any other model then feel free to replace it.<br/>
**Step – 5 Tuning**<br/>
To get the satisfied results, try to experiment on diffent parameters such as,<br/>
o	Batchsize<br/>
o	Dropout<br/>
o	learning rate<br/>
o	num_epochs <br/>
Or you can try this optimizers:<br/>
o	Nadam<br/>
o	Adam<br/>
o	RMSprop<br/>
o	SGD<br/>

# Results:
![Image of DatasetDistribution](https://image.prntscr.com/image/x36MhB11Sy6kyEb_c4yD6w.png)<br/>
# Dependencies:
Actually to follow this module you only need to install tensorflow, keras, scikit-learn with pip or conda command and you are good to go. But here some libraries that needed to be installed first that I use at this module :<br/>
o	PIL<br/>
o	Pandas<br/>
o	Numpy<br/>
o	Sklearn<br/>
o	Keras<br/>
o	tensorflow<br/>
