# Windows
I have tested the following versions of OS and softwares：
* OS：Win10
* Python 3.6.15

## Install (Please refer to [DOTA_devkit](https://github.com/CAPTAIN-WHU/DOTA_devkit) and [DOTA_devkit_YOLO](https://github.com/hukaixuan19970627/DOTA_devkit_YOLO))
a. Create a conda virtual environment and activate it, e.g.,
```
conda create -n dota python=3.6 -y 
conda activate dota
```
b. Install swig (Please refer to https://www.imooc.com/article/321766)

c. Install requirements.

```
numpy==1.19.1
pillow==7.2.0
opencv-python==4.1.2.30
matplotlib
shapely
```

```python 
pip install -r requirements.txt
```

d. Create the c++ extension for python

```python
swig -c++ -python polyiou.i
python setup.py build_ext --inplace
```

```c++
正在创建库 build\temp.win-amd64-3.6\Release\_polyiou.cp36-win_amd64.lib 和对象 build\temp.win-amd64-3.6\Release\_polyiou.cp36-win_amd64.exp
正在生成代码
已完成代码的生成
```
