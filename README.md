# Discriminative Region-based Multi-Label Zero-Shot Learning (ICCV 2021)
[[`arXiv`](https://arxiv.org/pdf/2108.09301.pdf)][[`webpage`](https://akshitac8.github.io/BiAM/)]

#### [Sanath Narayan](https://sites.google.com/view/sanath-narayan)<sup>\*</sup>, [Akshita Gupta](https://akshitac8.github.io/)<sup>\*</sup>, [Salman Khan](https://salman-h-khan.github.io/), [Fahad Shahbaz Khan](https://sites.google.com/view/fahadkhans/home), [Ling Shao](https://scholar.google.com/citations?user=z84rLjoAAAAJ&hl=en), [Mubarak Shah](https://scholar.google.com/citations?user=p8gsO3gAAAAJ&hl=en) ####

(:star2: denotes equal contribution)


## Installation
The codebase is built on PyTorch 1.1.0 and tested on Ubuntu 16.04 environment (Python3.6, CUDA9.0, cuDNN7.5).

For installing, follow these intructions
 
```
conda create -n mlzsl python=3.6
conda activate mlzsl
conda install pytorch=1.1 torchvision=0.3 cudatoolkit=9.0 -c pytorch
pip install matplotlib scikit-image scikit-learn opencv-python yacs joblib natsort h5py tqdm pandas
```
Install warmup scheduler

```
cd pytorch-gradual-warmup-lr; python setup.py install; cd ..

```

## Attention Visualization

<img src = "https://i.imgur.com/7D6Mi9u.png" width="900">

## Results
<table>
  <tr>
    <td> <img src = "https://i.imgur.com/DzhhRH0.png" width="400"> </td>
    <td> <img src = "https://i.imgur.com/B6XWZmR.png" width="450"> </td>
  </tr>
  <tr>
    <td><p align="center"><b>Our approach on NUS-WIDE Dataset.</b></p></td>
    <td><p align="center"><b>Our approach on OpenImages Dataset.</b></p></td>
  </tr>
</table>


## Training and Evaluation

### NUS-WIDE

### Step 1: Data preparation

1) Download pre-computed features and store them at `features` folder inside `BiAM/datasets/NUS-WIDE` directory.
2) [Optional] You can extract new features of any dimension by downloading original NUS-WIDE dataset from [here](https://lms.comp.nus.edu.sg/wp-content/uploads/2019/research/nuswide/NUS-WIDE.html) and running:

```
python feature_extraction/extract_nus_wide.py

```

### Step 2: Training from scratch

To train and evaluate multi-label zero-shot learning model on full NUS-WIDE dataset, please run:

```
sh scripts/train_nus.sh
```

### Step 3: Evaluation using pretrained weights

To evaluate the multi-label zero-shot model on NUS-WIDE. You can download the pretrained weights from (here)[] and store them at `NUS-WIDE` folder inside `pretrained_weights` directory.

```
sh scripts/evaluate_nus.sh
```

### OPEN-IMAGES

### Step 1: Data preparation

1) Please download the annotations for [training](https://storage.googleapis.com/openimages/2018_04/train/train-annotations-human-imagelabels.csv), [validation]( https://storage.googleapis.com/openimages/2018_04/validation/validation-annotations-human-imagelabels.csv), and [testing](https://storage.googleapis.com/openimages/2018_04/test/test-annotations-human-imagelabels.csv) into this folder.

2) Store the annotations inside `BiAM/datasets/OpenImages`.

3) Download pre-computed features and store them at `features` folder inside `BiAM/datasets/OpenImages` directory.

4) [Optional] You can extract new features by downloading original OpenImages-v4 dataset by running:

```
python ./datasets/OpenImages/download_imgs.py  #`data_set` == `train`: download images into `./image_data/train/`
python ./datasets/OpenImages/download_imgs.py  #`data_set` == `validation`: download images into `./image_data/validation/`
python ./datasets/OpenImages/download_imgs.py  #`data_set` == `test`: download images into `./image_data/test/`


python feature_extraction/extract_openimages_train.py
python feature_extraction/extract_openimages_test.py
python feature_extraction/extract_openimages_val.py

```

### Step 2: Training from scratch

To train and evaluate multi-label zero-shot learning model on full OpenImages dataset, please run:

```
sh scripts/train_openimages.sh
sh scripts/evaluate_openimages.sh

```

### Step 3: Evaluation using pretrained weights

To evaluate the multi-label zero-shot model on OpenImages. You can download the pretrained weights from (here)[] and store them at `OPENIMAGES` folder inside `pretrained_weights` directory.

```
sh scripts/evaluate_openimages.sh
```

## License
This repository is released under the Apache 2.0 license as found in the [LICENSE](LICENSE) file.

## Citation
If you find this repository useful, please consider giving a star :star: and citation :confetti_ball::

    @article{narayan2021discriminative,
    title={Discriminative Region-based Multi-Label Zero-Shot Learning},
    author={Narayan, Sanath and Gupta, Akshita and Khan, Salman and  Khan, Fahad Shahbaz and Shao, Ling and Shah, Mubarak},
    journal={Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)},
    publisher = {IEEE},
    year={2021}
    }

## Contact
Should you have any question, please contact :e-mail: akshita.gupta@inceptioniai.org
