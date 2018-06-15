# YOLOv3
Implementation of YOLOv3 in PyTorch.

## Overview
### YOLOv3: An Incremental Improvement
[[Paper]](https://pjreddie.com/media/files/papers/YOLOv3.pdf)   
[[Original Implementation]](https://github.com/pjreddie/darknet)   

### Why this project
Implement YOLOv3 and darknet53 without darknet format parser.   
It is easy to custom your backbone network. Such as resnet, densenet...   

## Installation
#### Environment
* pytorch >= 0.4.0
* python >= 3.6.0
#### Get code
```
git clone this repo
cd YOLOv3_PyTorch
pip3 install -r requirements.txt --user
```
#### Download COCO dataset
```
cd data/
bash get_coco_dataset.sh
```

## Training
##### Download pretrained weights
1. See [weights readme](weights/README.md) for detail.   
2. Download pretrained backbone wegiths from [Google Drive](https://drive.google.com/open?id=1VYwHUznM3jLD7ftmOSCHnpkVpBJcFIOA) or [Baidu Drive](https://pan.baidu.com/s/1axXjz6ct9Rn9GtDTust6DA)   
3. Move downloaded file ```darknet53_weights_pytorch.pth``` to ```wegihts``` folder in this project.   
##### Modify training parameters
1. Review config file ```training/params.py```   
2. Replace ```YOUR_WORKING_DIR``` to your working directory. Use for save model and tmp file.
3. Adjust your lr, parallels and so on.
##### Start training
```
cd training
python training.py params.py
```
##### Option: Visualizing training
You can using tensorbard to visualizing your training.   
But please install tensorboard in first.
```
python -m tensorboard.main --logdir=YOUR_WORKING_DIR   
```

## Evaluate
##### Download pretrained weights
1. See [weights readme](weights/README.md) for detail.   
2. Download pretrained yolo3 full wegiths from [Google Drive](https://drive.google.com/open?id=1Bm_CLv9hP3mMQ5cyerKRjvt7_t1duvjI) or [Baidu Drive](https://pan.baidu.com/s/1gx-XRUE1NTfIMKkQ1L0awQ)   
3. Move downloaded file ```yolov3_weights_pytorch.pth``` to ```wegihts``` folder in this project.   
##### Start evaluate
```
cd evaluate
python eval.py params.py
```
##### Results
| Model                      | mAP (min. 50 IoU) | weights file						 |
| -------------------------- |:-----------------:|:---------------------------------:|
| YOLOv3 (paper)             | 57.9              |							         |
| YOLOv3 (convert from paper)| 58.18             |official_yolov3_weights_pytorch.pth|
| YOLOv3 (train best model)  | 59.66             |yolov3_weights_pytorch.pth 		 |

## Credit
```
@article{yolov3,
	title={YOLOv3: An Incremental Improvement},
	author={Redmon, Joseph and Farhadi, Ali},
	journal = {arXiv},
	year={2018}
}
```

## Reference
* [darknet](https://github.com/pjreddie/darknet)
* [PyTorch-YOLOv3](https://github.com/eriklindernoren/PyTorch-YOLOv3): Thanks for Evaluate and YOLO loss code