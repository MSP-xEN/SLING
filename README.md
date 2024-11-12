# SLING
## 1. 创建conda环境
```
conda create -n habitat python=3.7 cmake=3.14.0
conda activate habitat
```
## 2. 安装0.2.1版本的 [habitat-sim](https://github.com/MSP-xEN/habitat-sim.git)
```
conda install habitat-sim=0.2.1 withbullet headless -c conda-forge -c aihabitat
```
## 3.安装[habitat-lab](https://github.com/facebookresearch/habitat-lab.git)
```
cd habitat-lab
pip install -r requirements.txt
python setup.py develop --all # install habitat and habitat_baselines
```
