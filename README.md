

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

<!--mask2former S Order mAP map05 map075 s m L
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
|------------------|----------|-------------|-------------|------------|------------|------------|----------|-------------|-------------|
| [SwinS-Mask2former](https://github.com/saidineshpola/MaskDINO-mapchallenge/blob/main/assets/logs/mask2former_swin-s-p4-w7-224_8xb2-lsj-50e_coco.log) | 0.380    | 0.721       | 0.382       | 0.152      | 0.495      | 0.692      | 0.504    | 0.879       | 0.509       |
| [SwinL-Mask2former](https://github.com/saidineshpola/MaskDINO-mapchallenge/blob/main/assets/logs/SWIN-L.log) | 0.3080   | 0.7260      | 0.2360      | 0.1710     | 0.4400     | 0.1310     | 0.453    | 0.855       | 0.464       |
| [RTMdet-M](https://github.com/saidineshpola/MaskDINO-mapchallenge/blob/main/assets/logs/rtmdet-ins_m_8xb32-300e_satellite.log) | 0.403    | 0.726       | 0.452       | 0.186      | 0.523      | 0.737      | 0.527    | 0.888       | 0.586       |
| [RTMdet-X](https://github.com/saidineshpola/MaskDINO-mapchallenge/blob/main/assets/logs/rtmdet-ins_X_8xb16-300e_satellite.log) | 0.418    | 0.743       | 0.472       | 0.194      | 0.536      | 0.769      | 0.529    | 0.897       | 0.586       |
| [QueryInst-r50](https://github.com/saidineshpola/MaskDINO-mapchallenge/blob/main/assets/logs/queryinst_r50_fpn_ms-3x_coco.log) | 0.400   | 0.711      | 0.437      | 0.188     | 0.517     | 0.657     | 0.553    | 0.905       | 0.595       |
| [QueryInst-r101](https://github.com/saidineshpola/MaskDINO-mapchallenge/blob/main/assets/logs/queryinst_r101_fpn_300_proposals_crop_mstrain_3x_coco.log) | 0.406   | 0.689      | 0.44      | 0.184     | 0.524     | 0.665     | 0.581    | 0.914       | 0.655       |
| **[MaskDINO](https://github.com/saidineshpola/MaskDINO-mapchallenge/tree/main/assets/logs)**     | **0.561**| **0.911**   | **0.650**   | **0.351**  | **0.6843** | **0.6851** | **0.617**| **0.949**    | **0.703**   |

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
