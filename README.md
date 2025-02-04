

# Mask DINO for MapChallenge Instance Segmentation

## Installation
See [installation instructions](INSTALL.md).

## Pretrained Model
Download the pretrained model:
[maskdino_swinl_50ep_300q_hid2048_3sd1_instance_maskenhanced_mask52.3ap_box59.0ap.pth](https://github.com/IDEA-Research/detrex-storage/releases/download/maskdino-v0.1.0/maskdino_swinl_50ep_300q_hid2048_3sd1_instance_maskenhanced_mask52.3ap_box59.0ap.pth)

## Training Command
```sh
python train_net.py \
     --num-gpus 2 \
     --config-file configs/coco/instance-segmentation/swin/maskdino_R50_bs16_50ep_4s_dowsample1_2048.yaml \
     MODEL.WEIGHTS maskdino_swinl_50ep_300q_hid2048_3sd1_instance_maskenhanced_mask52.3ap_box59.0ap.pth
```

## MapChallenge Instance Segmentation Results

| Model | segm mAP | segm mAP_50 | segm mAP_75 | segm mAP_s | segm mAP_m | segm mAP_l |
|-------|----------|-------------|-------------|------------|------------|------------|
| SwinS-Mask2former | 0.3110 | 0.7160 | 0.2180 | 0.1690 | 0.4420 | 0.0990 |
| SwinL-Mask2former | 0.3080 | 0.7260 | 0.2360 | 0.1710 | 0.4400 | 0.1310 |
| Rtmdet-X | 0.3910 | 0.7760 | 0.3440 | 0.2090 | 0.5440 | 0.2930 |
| RTMdet-M | 0.3790 | 0.7540 | 0.3170 | 0.2150 | 0.5210 | 0.2820 |
| QueryInst-r50 | 0.2770 | 0.6520 | 0.1830 | 0.1380 | 0.3890 | 0.1530 |
| QueryInst-r101 | 0.2780 | 0.6340 | 0.2000 | 0.1760 | 0.3910 | 0.1010 |
| **MaskDINO** | **0.5100** | **0.8690** | **0.5200** | **0.2740** | **0.6500** | **0.6560** |

## Additional Usage
For full usage and detailed instructions, refer to [Detectron2 Getting Started Guide](https://github.com/facebookresearch/detectron2/blob/master/GETTING_STARTED.md).

## Related repositories
- [mmdetection training experiments ](https://github.com/saidineshpola/mapchallenge-instance-segmentation/tree/main)
