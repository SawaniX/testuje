# Grasp planning
## Prerequsites:

1. Berkeley Autolab Core Modules - https://github.com/BerkeleyAutomation/autolab_core  
This module contains a set of useful utilities for robotic tasks.  
It is needed to run the next module.

2. Berkeley Autolab Perception Module - https://github.com/BerkeleyAutomation/perception  
This package provides a wide variety of useful tools for perception tasks.  
It is possible that previous module includes this module too.  
It is needed to generate .intr (camera intrinsics) file for the next module.

3. Berkeley AUTOLAB's GQCNN Package - https://github.com/BerkeleyAutomation/gqcnn  
The gqcnn package is a Python API for training and deploying Grasp Quality Convolutional Neural Networks (GQ-CNNs) for grasp planning.


## Installation

### Berkeley Autolab Core Modules
1. Clone source code from https://github.com/BerkeleyAutomation/autolab_core
  ``` sh
  $ cd {PATH_TO_YOUR_CATKIN_WORKSPACE}/src
  $ git clone https://github.com/BerkeleyAutomation/autolab_core.git
  ```  
2. Change directories into the autolab_core repository and run
  ``` sh
  $ python setup.py install
  ```  
3. Run catkin_make
  ``` sh
  $ cd {PATH_TO_YOUR_CATKIN_WORKSPACE}
  $ catkin_make
  ```  
4. Then re-source devel/setup.bash for the module to be available through Python.  
More informations: https://berkeleyautomation.github.io/autolab_core/index.html  

### Berkeley Autolab Perception Module
https://berkeleyautomation.github.io/perception/install/install.html  

### Berkeley AUTOLAB's GQCNN Package
1. Clone source code from https://github.com/BerkeleyAutomation/gqcnn
  ``` sh
  $ cd <PATH_TO_YOUR_CATKIN_WORKSPACE>/src
  $ git clone https://github.com/BerkeleyAutomation/gqcnn.git
  ```  

2. Build the catkin package
  ``` sh
  $ cd <PATH_TO_YOUR_CATKIN_WORKSPACE>
  $ catkin_make
  ```  

3. Then re-source devel/setup.bash for the package to be available through Python.  
More information: https://berkeleyautomation.github.io/gqcnn/


## Usage example
1. Start the grasp planning service
  ``` sh
  $ roslaunch gqcnn grasp_planning_service.launch model_name:=<model_name>
  ```  
  The args are:  
  - **model_name**: Name of the GQ-CNN model to use. Default is GQCNN-4.0-PJ.  
  - **model_dir**: Path to the directory where the GQ-CNN models are located. Default is models/. 
    If you are using the provided download_models.sh script, you shouldn’t have to modify this.  
    
2. To start the grasp planning service with the pre-trained Dex-Net 4.0 parallel jaw network run  
  ``` sh
  $ roslaunch gqcnn grasp_planning_service.launch model_name:=GQCNN-4.0-PJ
  ```  
  
3. The example ROS policy can then be queried on saved images using
  ``` sh
  $ python examples/policy_ros.py --depth_image <depth_image_filename> --segmask <segmask_filename> --camera_intr <camera_intr_filename>
  ```  
  The args are:
  - **depth_image_filename**: Path to a depth image (float array in .npy format).  
  - **segmask_filename**: Path to an object segmentation mask (binary image in .png format).  
  - **camera_intr_filename**: Path to a camera intrinsics file (.intr file generated with BerkeleyAutomation’s perception package).  
  
  
  
