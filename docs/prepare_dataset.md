

## NuScenes
Download nuScenes V1.0 full dataset (or mini dataset for a quick setup) data, CAN bus expansion data, and Map expansion data [HERE](https://www.nuscenes.org/download). Prepare nuscenes data as follows.


**Download CAN bus expansion**
```bash
cd ${PROJECT_DIR}/data
# download 'can_bus.zip' and unzip in `data` dir
unzip -q can_bus.zip
```

**Prepare nuScenes data (for training)**

*We generate custom annotation files which are different from mmdet3d's*

Directly download the [train](https://drive.google.com/file/d/1OVd6Rw2wYjT_ylihCixzF6_olrAQsctx/view?usp=sharing) file and [val](https://drive.google.com/file/d/16DZeA-iepMCaeyi57XSXL3vYyhrOQI9S/view?usp=sharing) file from google drive, or generate by yourself:
```shell
cd ${PROJECT_DIR}
python tools/data_converter/vad_nuscenes_converter.py nuscenes --root-path ./data/nuscenes --out-dir ./data/nuscenes --extra-tag vad_nuscenes --version v1.0 --canbus ./data
```

Using the above code will generate `vad_nuscenes_infos_temporal_{train,val}.pkl`.

**Prepare nuScenes mini dataset (for quick evaluation)**

```shell
cd ${PROJECT_DIR}/data
mkdir nuscenes-mini
tar -xf nuScenes_v1.0-mini.tgz -C nuscenes-mini
```

*We generate custom annotation files which are different from mmdet3d's*

```shell
cd ${PROJECT_DIR}
python tools/data_converter/vad_nuscenes_converter.py nuscenes --root-path ./data/nuscenes-mini --out-dir ./data/nuscenes-mini --extra-tag vad_nuscenes_mini --version v1.0-mini --canbus ./data
```

Using the above code will generate `vad_nuscenes_mini_infos_temporal_{train,val}.pkl`.

**Download Map expansion (for nuScenes mini)**
```bash
cd ${PROJECT_DIR}/data
# download 'nuScenes-map-expansion-v1.3.zip' and unzip in `data/nuscenes-mini/maps` dir
unzip -q nuScenes-map-expansion-v1.3.zip -d nuscenes-mini/maps/
```

**Folder structure**
```
VAD
├── projects/
├── tools/
├── configs/
├── ckpts/
│   ├── resnet50-19c8e357.pth
├── data/
│   ├── can_bus/
│   ├── nuscenes/
│   │   ├── maps/
│   │   ├── samples/
│   │   ├── sweeps/
│   │   ├── v1.0-test/
│   │   ├── v1.0-trainval/
│   │   ├── vad_nuscenes_infos_temporal_train.pkl
│   │   ├── vad_nuscenes_infos_temporal_val.pkl
│   ├── nuscenes-mini/
│   │   ├── maps/
│   │   ├── samples/
│   │   ├── sweeps/
│   │   ├── v1.0-mini/
│   │   ├── vad_nuscenes_mini_infos_temporal_train.pkl
│   │   ├── vad_nuscenes_mini_infos_temporal_val.pkl
```
