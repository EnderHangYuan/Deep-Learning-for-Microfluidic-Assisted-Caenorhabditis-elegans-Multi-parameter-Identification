# Deep-Learning-for-Microfluidic-Assisted-Caenorhabditis-elegans-Multi-parameter-Identification-using-YOLOv7
Author list:

Jie Zhang 1,2 †, Shuhe Liu 1 †, Hang Yuan 1 †, Ruiqi Yong 1, Sixuan Duan 1,2, Yifan Li 1,2, Joseph Spencer 2, Eng Gee Lim 1,2*, Limin Yu 1,2*, Pengfei Song 1,2*

1	School of Advanced Technology, Xi'an Jiaotong - Liverpool University, Suzhou, Jiangsu 215123, China

2	Department of Electrical and Electronic Engineering, University of Liverpool, Liverpool L693BX, UK

*Correspondence: enggee.lim@xjtlu.edu.cn; limin.yu@xjtlu.edu.cn; Pengfei.Song@xjtlu.edu.cn;

† Jie Zhang, Shuhe Liu and Hang Yuan contributed equally to this work.

### Note: The dataset used can be found on [Zenodo](https://zenodo.org/record/7714497).

# Training Steps:
1. Dataset Preparation:
In this paper, the training is conducted using the VOC format. Prior to training, it is necessary to prepare the dataset by placing the label files in the `Annotation` folder, located within the `VOC2007` folder, which is in turn placed under the `VOCdevkit` folder. Similarly, the image files should be placed in the `JPEGImages` folder, also located within the `VOC2007` folder under the `VOCdevkit` directory.
2. Dataset Processing:
After arranging the dataset, we need to use `voc_annotation.py` to obtain the `2007_train.txt` and `2007_val.txt` files for training. Modify the parameters in `voc_annotation.py`. For the initial training, you can simply modify the `classes_path` parameter, which points to the txt file corresponding to the detection classes. When training your own dataset, you can create a `cls_classes.txt` file and list the categories you want to distinguish. The content of the `model_data/cls_classes.txt` file should be: cat, dog... Modify the `classes_path` in `voc_annotation.py` to correspond to `cls_classes.txt` and run `voc_annotation.py`.
3. Network Training:
There are multiple training parameters, all of which can be found in `train.py`. After downloading the repository, it is important to carefully read the comments within the file. The most crucial part is still the `classes_path` in `train.py`. `classes_path` points to the txt file corresponding to the detection classes, which should be the same as the one used in `voc_annotation.py`! It is necessary to modify it when training your own dataset. Once the `classes_path` is modified, you can run `train.py` to start the training process. After training for several epochs, the weights will be generated in the `logs` folder.
4. Prediction of Training Results:
The prediction of training results requires two files, namely `yolo.py` and `predict.py`. In `yolo.py`, modify the `model_path` and `classes_path`. `model_path` points to the trained weight file, located in the `logs` folder. `classes_path` points to the txt file corresponding to the detection classes. Once the modifications are completed, you can run `predict.py` for detection. After running, input the image path to perform detection.

# Prediction Steps:

Follow the training steps to train the model. In the `yolo.py` file, modify the `model_path` and `classes_path` to correspond to the trained files: The `model_path` corresponds to the weight file under the `logs` folder, and the `classes_path` lists the classes associated with the `model_path`. Perform FPS testing and video detection by running `predict.py`, inputting `img/street.jpg`, and configuring the settings within `predict.py`.
