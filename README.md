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
## 3.安装[habitat-lab](https://github.com/facebookresearch/habitat-lab.git) SLING所需要[habitat-lab](https://github.com/Jbwasse2/SLING.git)略有不同，需要从requirement文件下载
```
cd habitat-lab
pip install -r requirements.txt
python setup.py develop --all # install habitat and habitat_baselines
```
## 4. 将`src`文件夹添加到pythonpath
```
export PYTHONPATH=${PYTHONPATH}:/path/to/src/folder/
```
## 5. 安装必需的checkpoint文件（需要安装gdown以及良好的网络环境，需要能够连接谷歌服务器）
```gdown 1OfJ3fMo7II1lNUZs743zalBMSV71JeDC
unzip checkpoint.zip

gdown 1KJ0XHLlg9CxgPBG7OAM1c8L9ZG4AKzxv
unzip data.zip

gdown 1bR4bH7-OrDqo7TItwBcg4BS0Ls08Z1vl
unzip models.zip
```
## 6. 将这些文件移到合适的位置
```
mv gibson_train_val embodied_ssl/data/scene_datasets/
mv mp3d embodied_ssl/data/scene_datasets/
```
## 7. 安装必要的数据集[Gibson](https://docs.google.com/forms/d/e/1FAIpQLScWlx5Z1DM1M-wTSXaa6zV8lTFkPmTHW1LqMsoCBDWsTDjBkQ/viewform?pli=1)以及[Mp3D](https://niessner.github.io/Matterport/) (下载数据集需要验证）
将数据集移动到指定位置
```
mv gibson_train_val embodied_ssl/data/scene_datasets/
mv mp3d embodied_ssl/data/scene_datasets/
```
## 8. 修改`sbatch_scripts/run_script.sh`第5行的变量使其指向实际文件
REPO_PATH=/path/to/code/embodied_ssl
## 9. 运行下列指令
```
./sbatch_scripts/run_ovrl.sh
./sbatch_scripts/run_ddppo.sh
```
