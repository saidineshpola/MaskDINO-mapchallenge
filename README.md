

# Mask DINO for MapChallenge Instance Segmentation

## Installation
See [installation instructions](INSTALL.md).

## Pretrained Model
Download the pretrained model:
[maskdino_swinl_50ep_300q_hid2048_3sd1_instance_maskenhanced_mask52.3ap_box59.0ap.pth](https://github.com/IDEA-Research/detrex-storage/releases/download/maskdino-v0.1.0/maskdino_swinl_50ep_300q_hid2048_3sd1_instance_maskenhanced_mask52.3ap_box59.0ap.pth)

## Training 
```sh
python train_net.py \
     --num-gpus 2 \
     --config-file configs/coco/instance-segmentation/swin/maskdino_R50_bs16_50ep_4s_dowsample1_2048.yaml \
     MODEL.WEIGHTS maskdino_swinl_50ep_300q_hid2048_3sd1_instance_maskenhanced_mask52.3ap_box59.0ap.pth
```
## Evaluation
```sh
python train_net.py \
     --eval-only \
     --num-gpus 2 \
     --config-file configs/coco/instance-segmentation/swin/maskdino_R50_bs16_50ep_4s_dowsample1_2048.yaml \
     DATASETS.TEST '("satellite_test",)' \
     MODEL.WEIGHTS MODEL_CHECKPOINT_PATH
```

<!--mask2former S 
segm_mAP_copypaste: 0.380 0.721 0.382 0.152 0.495 0.692
segm_mAR_copypaste:0.504 0.879 0.509 0.338 0.594 0.783 

rtmdet-m
segm_mAP_copypaste: 0.403 0.726 0.452 0.186 0.523 0.737
segm_mAR_copypaste: 0.527 0.888 0.586 0.351 0.622 0.817

rtmdet-X
segm_mAP_copypaste: 0.418 0.743 0.472 0.194 0.536 0.769
segm_mAR_copypaste: 0.529 0.897 0.586 0.358 0.617 0.867 
 -->
## MapChallenge Instance Segmentation Results

| Model            | segm mAP | segm mAP@50 | segm mAP@75 | segm mAP_s | segm mAP_m | segm mAP_l | segm mAR | segm mAR@50 | segm mAR@75 |
|------------------|----------|-------------|-------------|------------|------------|------------|---------|--------|------------|
| SwinS-Mask2former| 0.3800   | 0.7210      | 0.3820      | 0.1520     | 0.4950     | 0.6920     | 0.5040  | 0.8790 | 0.5090     |
| SwinL-Mask2former| 0.4030   | 0.7260      | 0.4520      | 0.1860     | 0.5230     | 0.7370     | 0.5270  | 0.8880 | 0.5860     |
| Rtmdet-X         | 0.4180   | 0.7430      | 0.4720      | 0.1940     | 0.5360     | 0.7690     | 0.5290  | 0.8970 | 0.5860     |
| RTMdet-M         | 0.3910   | 0.7260      | 0.4520      | 0.1860     | 0.5230     | 0.7370     | 0.5270  | 0.8880 | 0.5860     |
| QueryInst-r50    | 0.2770   | 0.6520      | 0.1830      | 0.1380     | 0.3890     | 0.1530     | 0.4320  | 0.8260 | 0.3840     |
| QueryInst-r101   | 0.2780   | 0.6340      | 0.2000      | 0.1760     | 0.3910     | 0.1010     | 0.4580  | 0.8550 | 0.4640     |
| **MaskDINO**     | **0.561** | **0.911**    | **0.650**   | **0.351**   | **0.6843** | **0.6851** | **0.617** | **0.949** | **0.703**  |
<br>

**Note:**
- **mAP@50/mAR@50** refers to average precision/recall at 0.50 and **mAP@75/mAR@75** refers to average precision/recall at 0.75 IOU
- `segm mAP` values are usually averaged over multiple IOUs from 0.5 to 0.95 with interval of 0.05
- In metric columns,
       - `s` = small objects
       - `m` = medium objects
       - `l` = large objects
## Additional Usage
For full usage and detailed instructions, refer to [Detectron2 Getting Started Guide](https://github.com/facebookresearch/detectron2/blob/master/GETTING_STARTED.md).

## Related repositories
- [mmdetection training experiments ](https://github.com/saidineshpola/mapchallenge-instance-segmentation/tree/main)
