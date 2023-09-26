# SLC-Net
This repository is for our paper 'Semi-supervised medical image segmentation using cross-style
consistency with shape-aware and local context constraints'

## Requirements
Some important required packages include:

* Pytorch version >=0.4.1.

* TensorBoardX

* Python == 3.7

* Efficientnet-Pytorch

* Some basic python packages such as Numpy, Scikit-image, SimpleITK, Scipy，Batchgenerators ......

## Usage

### 1、Clone the repo.;
```
git clone https://github.com/igip-liu/SLC-Net.git
```

### 2、Data Preparation;

The division method of training set/validation set/test set can be seen:

[ACDC dataset](https://github.com/igip-liu/SLC-Net/tree/main/data/ACDC)

[Prostate dataset](https://github.com/igip-liu/SLC-Net/tree/main/data/Prostate)

[LA dataset](https://github.com/yulequan/UA-MT/tree/master/data)

The processed data that can be used to train our code can be seen:

[ACDC dataset](https://github.com/igip-liu/SLC-Net/tree/main/data/ACDC/data)

[Prostate dataset](https://github.com/igip-liu/SLC-Net/tree/main/data/Prostate/data)

[LA dataset](https://github.com/yulequan/UA-MT/tree/master/data)

The division of labeled/unlabeled datasets can be found in [this code](https://github.com/igip-liu/SLC-Net/blob/main/code/train_CLB.py)

You can regenerate the training data:
```
cd SLC-Net/code/dataloaders

python acdc_data_processing.py
```
### 3、Train the model;

```
cd SLC-Net/code

CUDA_VISIBLE_DEVICES=3 python train_CLB.py --root_path ../data/ACDC --exp ACDC/SLC-Net --num_classes 4 --labeled_num 7 --use_block_dice_loss --block_num 4
```
### 4、Test the model;
```
cd SLC-Net/code

CUDA_VISIBLE_DEVICES=0 python test_2D_fully.py --root_path ../data/ACDC --exp ACDC/SLC-Net --num_classes 4 --labeled_num 7
```
Our code is based on the [UAMT](https://github.com/yulequan/UA-MT), [SSL4MIS](https://github.com/HiLab-git/SSL4MIS) and [Dual-Normalization](https://github.com/zzzqzhou/Dual-Normalization). Thanks for these authors for their valuable works.