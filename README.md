# YOLOv7 model trained on cattle muzzle detection

Implementation of paper - [YOLOv7: Trainable bag-of-freebies sets new state-of-the-art for real-time object detectors](https://arxiv.org/abs/2207.02696)

To run the model, download the weights from [here](https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt) and place it in the `root` folder.

## Training

```shell
    conda create -n yolov7 python=3.9
    conda activate yolov7
    pip install -r requirements.txt
    pip install -r requirement_gpu.txt # for gpu
    python train.py --workers 1 --device 0 --batch-size 8 --epochs 100 --img 640 640 --data data/coco.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/yolov7-w6.yaml --weights yolov7_training.pt 
    #increase batch size if gpu memory is high (>12GB)
```

Training will roughly take 6 hours or more depending on your GPU (6h on RTX 2060)

## Testing

```shell
    python test.py --weights runs/train/exp/weights/best.pt --data data/coco.yaml --img 640 540 --iou 0.65 --device 0 --batch-size 8
    #increase batch size if GPU memory is high
    #Change IOU confidence level as per need, default is 0.65
```