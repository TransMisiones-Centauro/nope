<div align="center">
<h3>
NOPE: Novel Object Pose Estimation from a Single Image
<p></p>
</h3>

<h4>
<a href="https://nv-nguyen.github.io/" target="_blank"><nobr>Van Nguyen Nguyen</nobr></a> &emsp;
<a href="http://imagine.enpc.fr/~groueixt/" target="_blank"><nobr>Thibault Groueix</nobr></a> &emsp;
<a href="hhttps://scholar.google.com/citations?user=5G-6ubcAAAAJ" target="_blank"><nobr>Georgy Ponimatkin</nobr></a> &emsp;
<a href="https://yinlinhu.github.io/" target="_blank"><nobr>Yinlin Hu</nobr></a> &emsp; <br>
<a href="https://imagine.enpc.fr/~marletr/" target="_blank"><nobr>Renaud Marlet</nobr></a> &emsp;
<a href="https://people.epfl.ch/mathieu.salzmann" target="_blank"><nobr>Mathieu Salzmann</nobr></a> &emsp;
<a href="https://vincentlepetit.github.io/" target="_blank"><nobr>Vincent Lepetit</nobr></a>

<p></p>

<a href="https://nv-nguyen.github.io/nope/"><img 
src="https://img.shields.io/badge/-Webpage-blue.svg?colorA=333&logo=html5" height=22em></a>
<a href="https://arxiv.org/abs/2303.13612"><img 
src="https://img.shields.io/badge/-Paper-blue.svg?colorA=333&logo=arxiv" height=22em></a>
<p></p>

<p align="center">
  <img src=./media/result.gif width="60%"/>
</p>

</h3>
</div>

If our project is helpful for your research, please consider citing : 
```latex
@inproceedings{nguyen2024nope,
title={{NOPE: Novel Object Pose Estimation from a Single Image}},
author={Nguyen, Van Nguyen and Groueix, Thibault and Ponimatkin, Georgy and Hu, Yinlin and Marlet, Renaud and Salzmann, Mathieu and Lepetit, Vincent},
booktitle={{Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition}}
year=2024
}
```
You can also put a star :star:, if the code is useful to you.

If you like this project, check out related works from our group:
- [GigaPose: Fast and Robust Novel Object Pose Estimation via One Correspondence (CVPR 2024)](https://github.com/nv-nguyen/gigaPose) 
- [CNOS: A Strong Baseline for CAD-based Novel Object Segmentation (ICCVW 2023)](https://github.com/nv-nguyen/cnos) 
- [Templates for 3D Object Pose Estimation Revisited: Generalization to New objects and Robustness to Occlusions (CVPR 2022)](https://github.com/nv-nguyen/template-pose) 
- [PIZZA: A Powerful Image-only Zero-Shot Zero-CAD Approach to 6DoF Tracking (3DV 2022)](https://github.com/nv-nguyen/pizza)


![Teaser image](./media/framework.png)

Abstract: *The practicality of 3D object pose estimation remains limited for many applications due to the need for prior knowledge of a 3D model and a training period for new objects. To address this limitation, we propose an approach that takes a single image of a new object as input and predicts the relative pose of this object in new images without prior knowledge of the object’s 3D model and without requiring training time for new objects and categories. We achieve this by training a model to directly predict discriminative embeddings for viewpoints surrounding the object. This prediction is done using a simple U-Net architecture with attention and conditioned on the desired pose, which yields extremely fast inference. We compare our approach to state-of-the-art methods and show it outperforms them both in terms of accuracy and robustness.*


## Installation :construction_worker:

<details><summary>Click to expand</summary>

This repository is running with the Weight and Bias logger. Ensure that you update this [user's configuration](https://github.com/nv-nguyen/nope/blob/main/configs/user/default.yaml) before conducting any experiments. 

### 1. Create conda environment
```
conda env create -f environment.yml
conda activate nope
```

### 2. Datasets
Please note that the total dataset size is huge (~2TB). Before running the following commands, ensure that you have sufficient memory to handle this volume of data.

#### Option 1: Render dataset from scratch:
```
python -m src.scripts.generate_data --step select_cad --cad_dir $YOUR_CAD_DIR --save_dir $YOUR_SAVE_DIR
python -m src.scripts.generate_data --step generate_poses_and_images --cad_dir $YOUR_CAD_DIR --save_dir $YOUR_SAVE_DIR
```

#### Option 2: Contact the first authors to get the pre-rendered dataset
Rendering the dataset from scratch may take several days or even a week, depending on your compute power. To facilitate easy reproducibility and experimentation with this repository, you can contact the first author to manage transferring the dataset (over SSH for example).

</details>

##  Inference

<details><summary>Click to expand</summary>

```
python test_shapeNet.py name_exp=test_shapeNet
```

</details>

##  Launch a training :rocket:

<details><summary>Click to expand</summary>

```
python train.py name_exp=train
```

</details>

