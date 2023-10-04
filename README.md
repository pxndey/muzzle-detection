# YOLOv7 model trained on cattle muzzle detection

Cloned and used from [The Official YOLOv7 Repository](https://github.com/WongKinYiu/yolov7)

Implementation of paper - [YOLOv7: Trainable bag-of-freebies sets new state-of-the-art for real-time object detectors](https://arxiv.org/abs/2207.02696)

To run the model, download the weights file from [here](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt) and place in the `root` folder.

## Prerequisites

Run these commands one by one when the Conda terminal is active:

```shell
    #Create conda environment and install dependencies
    conda create -n yolov7 python=3.9
    conda activate yolov7
    pip install -r requirements.txt
    pip install -r requirement_gpu.txt # for gpu

```

## Training

```shell
    python train.py --workers 1 --device 0 --batch-size 8 --epochs 100 --img 640 640 --data data/coco.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/yolov7-w6.yaml --weights yolov7_training.pt 
    #increase batch size if gpu memory is high (>12GB)
```

Training will roughly take 6 hours or more depending on your GPU (6 hours on RTX 2060)

After training move the **best.pt** file from _runs/train/exp/weights_ to the root folder where the repository resides

## Testing

```shell
    python test.py --weights best.pt --data data/coco.yaml --img 640 --iou 0.65 --device 0 --batch-size 8 --task test --save-txt --save-conf
    #increase batch size if GPU memory is high
    #Change IOU confidence level as per need, default is 0.65
```
