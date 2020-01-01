
## Install

- Get miniconda installer sh from (https://conda.io/miniconda.html)[https://conda.io/miniconda.html]
```
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
- Run shell script (change permission if needed)
```
./Miniconda3-latest-Linux-x86_64.sh
```
Default install location will be /home/[username]/miniconda3


## Create Environment
-
```
conda create -n myenv python
```
- Activate
```
source activate appname
```
- Deactivate
```
source deactivate
```
- Show conda environments
```
conda env list
```
