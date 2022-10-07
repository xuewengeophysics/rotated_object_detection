# Windows
I have tested the following versions of OS and softwares：
* OS：Win10
* CUDA Version: 11.4
* CUDA Toolkit Version: release 11.3, V11.3.109
* Python 3.9.13
* PyTorch: 1.10.1+cu113

## Install (Please refer to this [github](https://github.com/hukaixuan19970627/yolov5_obb))
**CUDA Driver Version ≥ CUDA Toolkit Version(runtime version) = torch.version.cuda**

a. Create a conda virtual environment and activate it, e.g.,
```
conda create -n pth10 python=3.9 -y 
conda activate pth10
```
b. Make sure your CUDA runtime api version ≤ CUDA driver version. (for example 11.3 ≤ 11.4)
```
nvcc -V
nvidia-smi
```
c. Install PyTorch and torchvision following the [official instructions](https://pytorch.org/), Make sure cudatoolkit version same as CUDA runtime api version, e.g.,
```
pip3 install torch==1.10.1+cu113 torchvision==0.11.2+cu113 torchaudio==0.10.1+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
nvcc -V
python
>>> import torch
>>> torch.version.cuda
'11.3'
```
d. Clone the yolov5-obb repository.
```
git clone https://github.com/hukaixuan19970627/yolov5_obb.git
cd yolov5_obb
```
e. Install yolov5-obb.

```python 
pip install -r requirements.txt
cd utils/nms_rotated
python setup.py develop  #or "pip install -v -e ."
```

f. Debug

```python
D:\yolov5_obb\utils\nms_rotated\src\poly_nms_cuda.cu(27): error: identifier "eps" is undefined in device code

D:\yolov5_obb\utils\nms_rotated\src\poly_nms_cuda.cu(27): error: identifier "eps" is undefined in device code

2 errors detected in the compilation of "src/poly_nms_cuda.cu".
error: command 'C:\\Program Files\\NVIDIA GPU Computing Toolkit\\CUDA\\v11.3\\bin\\nvcc.exe' failed with exit code 1
```

g. Modify "utils/nms_rotated/src/poly_nms_cuda.cu" (Please refer to this [issue](https://github.com/hukaixuan19970627/yolov5_obb/issues/149))

```c++
#define maxn 10
//const double eps=1E-8;

__device__ inline int sig(float d){
    //return(d>eps)-(d<-eps);
	return(d>1E-8)-(d<-1E-8);
}
```

h. Recompile

```python
python setup.py develop  #or "pip install -v -e ."
```

```python
Processing dependencies for nms-rotated==0.0.0
Finished processing dependencies for nms-rotated==0.0.0
```

