# Human Pose-Estimation Using Jetson/NX

## Introduction
Human Pose Estimation (HPE) is a way of identifying and classifying the joints in the human body.

Essentially it is a way to capture a set of coordinates for each joint (arm, head, torso, etc.,) which is known as a key point that can describe a pose of a person. The connection between these points is known as a pair. 

## Installation Guide

### Step 1: Setting Up OS on Jetson Device

1. Install Jetpack/OS on Jetson Device [guide](https://developer.nvidia.com/embedded/learn/get-started-jetson-xavier-nx-devkit).
2. After installing Jetpack on Jetson Device, follow the basic system configuration.

### Step 2: Install Virtual Environment

1. On Jetson Device Open Terminal (Ctrl+T) and run the following command
  ```python
    sudo apt-get update && upgrade
    sudo apt-get install python3-dev python3-pip
    pip3 install -U virtualenv
  ```

2. Create Virtual Environment
  ```python  
  python3 -m virtualenv --system-site-packages /home/Your-Jetson-UserName/python
  ```
  Activate the virtual environment using the following command. </br>
  ```Python
  source /home/Your-Jetson-UserName/python/bin/activate
  ```

### Step 3: Install Torch & Torchvision
#### Torch Installation
1. Inside The Virtual Environment Install the Following.
  ```python
  sudo apt-get install python3-pip libopenblas-base libopenmpi-dev
  sudo apt-get install wget
  wget https://nvidia.box.com/shared/static/yr6sjswn25z7oankw8zy1roow9cy5ur1.whl -O torch-1.6.0-cp36-cp36m-linux_aarch64.whl
  pip3 install Cython
  pip3 install torch-1.6.0-cp36-cp36m-linux_aarch64.whl
  ```
#### Torchvision Installation
1. Inside The Virtual Environment Install the Following.
  ```python
  sudo apt-get install libjpeg-dev zlib1g-dev
  wget https://github.com/pytorch/vision/archive/v0.6.1.tar.gz
  tar -zxvf v0.6.1.tar.gz
  cd vision-0.6.1
  python3 setup.py install
  sudo apt-get install libfreetype6-dev
  pip3 uninstall pillow
  pip3 install --no-cache-dir pillow
  ```
### Step 4: Setup Torch2TRT, TRT-Pose & Human-Pose
1. Create a Directory name src in the Home Dierectory and Save the Torch2TRT, TRT-Pose & Human-Pose.
  ```python
  sudo mkdir src
  cd src/(save all the files)
  ```
#### Setting Up Torch2TRT
  ```python
  cd src/tort2trt
  sudo apt-get install python3-matplotlib
  pip3 install tqdm cython pycocotools
  python3 setup.py install
  ```
#### Setting Up TRT-Pose
  ```python
  cd ../trt_pose
  python3 setup.py install
  ```
#### Setting Up Human-Pose
  ```python
  cd ../human_pose
  python3 setup.py install
  ```
### Step 5: Run HPE
1. Open terminal & Activate Virtual Environment
  ```python
  source /home/Your-Jetson-UserName/python/bin/activate
  ```
2. Change Directory to: src/trt_pose/tasks/human_pose/
  ```python
  cd src/trt_pose/tasks/human_pose/
  python3 final_code_modify_changed_2_final.py
  ```
#
