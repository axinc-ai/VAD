# Step-by-step installation instructions

Following https://mmdetection3d.readthedocs.io/en/latest/getting_started.html#installation.

Detailed package versions can be found in [requirements.txt](../requirements.txt).



**a. Create a conda virtual environment and activate it.**
```shell
conda create -n vad python=3.8 -y
conda activate vad
```

**b. Install PyTorch and torchvision following the [official instructions](https://pytorch.org/).**
```shell
pip install torch==1.9.1+cu111 torchvision==0.10.1+cu111 torchaudio==0.9.1 -f https://download.pytorch.org/whl/torch_stable.html
# Recommended torch>=1.9
```

**c. Install gcc>=5 in conda env (optional).**
```shell
conda install -c omgarcia gcc-5 # gcc-6.2
```

**c. Install mmcv-full.**
```shell
pip install mmcv-full==1.4.0
#  pip install mmcv-full==1.4.0 -f https://download.openmmlab.com/mmcv/dist/cu111/torch1.9.0/index.html
```

**d. Install mmdet and mmseg.**
```shell
pip install mmdet==2.14.0
pip install mmsegmentation==0.14.1
```

**e. Install timm.**
```shell
pip install timm
```

**f. Install nuscenes-devkit.**
```shell
pip install nuscenes-devkit==1.1.9
```

**g. Install mmdet3d.**
```shell
git clone https://github.com/open-mmlab/mmdetection3d.git
cd mmdetection3d
git checkout -f v0.17.1
pip install -v -e .  # Takes time to build
cd -
```

**h. Install other dependencies.**
```shell
pip install similaritymeasures==0.7.0
pip install -U Shapely==1.8.5  # Downgrade to solve issue #29
```

**i. Clone VAD.**
```shell
git clone https://github.com/hustvl/VAD.git
cd VAD
PROJECT_DIR=$(pwd)
mkdir data
```

**j. Prepare pretrained models.**
```shell
cd ${PROJECT_DIR}
mkdir ckpts
cd ckpts
wget https://download.pytorch.org/models/resnet50-19c8e357.pth  # For training
# Place VAD_base and VAD_tiny pretrained models in this `ckpts` folder too.
```
