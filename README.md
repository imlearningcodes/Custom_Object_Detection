# Custom_Object_Detection
The project aims to use Image processing in Python that will help in making a Smart Animal Detection System.

Training YOLO algorithm for animal detection using OIDV4 toolkit
In this method, a custom dataset of YOLO is trained using OIDV4 toolkit and then modeled train it in the cloud.
The tools we used here are-
1.	Python library
2.	OIDV4 toolkit
3.	Google Colaboratory with free GPU


The method is discussed below-
1.	Using OIDV4 toolkit
Starting from the terminal, python library is required and it is to be installed using pip. Then cloning the repository is required from github. There are few packages which are to be installed along with this.
Next, the Toolkit is used to download classes in separated folders. The argument --classes accepts a list of classes or the path to the file.txt (--classes path/to/file.txt) that contains the list of all classes one for each lines (classes.txt uploaded as example).
The algorithm will take care to download all the necessary files and build the directory structure like the fig:  (taking an example of class Apple). Comma Separated Value(CSV) files are also to be downloaded and put in the csv folder. Multiple classes can also be downloaded into a same folder by using multi-classes option while accessing the toolkit.


Next, annotations are considered. In the original dataset the coordinates of the bounding boxes are made in the following way:
XMin, XMax, YMin, YMax: coordinates of the box, in normalized image coordinates. XMin is in [0,1], where 0 is the leftmost pixel, and 1 is the rightmost pixel in the image. Y coordinates go from the top pixel (0) to the bottom pixel (1). (Fig :) However, in order to accomodate a more intuitive representation and give the maximum flexibility, every .txt annotation is made where each coordinate is denormalized. So, the four different values correspond to the actual number of pixels of the related image.


The Toolkit is now able to access also to the huge dataset without bounding boxes. This dataset is formed by 19,995 classes and it's already divided into train, validation and test. The command used for the download from this dataset is downloader_ill (Downloader of Image-Level Labels) and requires the argument --sub. This argument selects the sub-dataset between human-verified labels h (5,655,108 images) and machine-generated labels m (8,853,429 images).
The Toolkit is useful also for visualize the downloaded images with the respective labels.
After achieving the dataset, next we copy these data into a folder in Google drive.

2.	Training the model in Cloud VM
Here, the cloud virtual machine used is Google Colab. The steps involved here are simple. Firstly, GPU is enabled within the Colab notebook using the hardware accelerator. Then darknet is cloned and built and adjusted the makefile to enable OpenCV and python.
YOLOv3 has been trained already on the coco dataset which has 80 classes that it can predict. These pretrained weights are taken into account so that YOLO V3 can run on these pretrained classes and get detections. Darknet is built and ready to run detections using YOLOv3 in the cloud.

Nextly, Images are uploaded to the cloud VM from Google Drive, but before that mounting or linking of the VM to the drive has to be done.

Next step involves properly configuring the custom .cfg file, obj.data, obj.names and train.txt file.
The cfg or configurations file has to be edited for the suitable number of classes and iterations required and its subdivisions and batch is defined. Also object data and object names which would contain the information of classes used and names of classes required respectively.
The last configuration file needed is the train.txt file which hold the relative paths to all training images.
Finally, the weights for the convolutional layers of the YOLOv3 network are downloaded. Then the training is done using a simple python code.


