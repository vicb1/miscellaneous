#### install cuda 10.2.89, cudnn 7.6.5.32, and tensorflow 2.4, to match kaggle

per: https://forums.developer.nvidia.com/t/installing-cuda-10-2-on-ubuntu-18-04-3/107773
and: https://askubuntu.com/questions/1260039/how-to-install-specific-nvidia-driver-like-nvidia-driver-440-440-33-01-deb
```
sudo apt-get purge *nvidia*
sudo apt autoremove
sudo rm -rf /usr/lib/cuda  # to remove previous cudnn files
sudo add-apt-repository ppa:graphics-drivers/ppa -y 
sudo apt update -y 
sudo apt-get update
sudo apt install nvidia-driver-440 -y 
*restart*
*change to driver-440 in program Software & updates*
*restart*
sudo apt install nvidia-cuda-toolkit
*restart*
nvidia-smi
nano ~/.bashrc
echo 'export CUDA_PATH=/usr' >> ~/.bashrc
nano ~/.bashrc
source ~/.bashrc
```

Using cudnn:
https://developer.nvidia.com/compute/machine-learning/cudnn/secure/7.6.5.32/Production/10.2_20191118/cudnn-10.2-linux-x64-v7.6.5.32.tgz

Install cudnn per:
https://askubuntu.com/questions/1230645/when-is-cuda-gonna-be-released-for-ubuntu-20-04

https://stackoverflow.com/questions/65273118/why-is-tensorflow-not-recognizing-my-gpu-after-conda-install


### install cuda 11, cudnn 8, tensorflow 2.4
https://www.tensorflow.org/install/source#gpu
need cuda 11, cudnn 8, tensorflow 2.4

per https://askubuntu.com/questions/1288672/how-do-you-install-cuda-11-on-ubuntu-20-10-and-verify-the-installation
```
sudo apt-get purge *nvidia*
sudo apt autoremove
sudo apt-get update
sudo apt install nvidia-driver-455
*restart*
nvidia-smi
sudo apt install nvidia-cuda-toolkit
nano ~/.bashrc
echo 'export CUDA_PATH=/usr' >> ~/.bashrc
nano ~/.bashrc
source ~/.bashrc
```

10.1 version when running `nvcc --version`, but this is ok because:
https://stackoverflow.com/questions/53422407/different-cuda-versions-shown-by-nvcc-and-nvidia-smi

Using cudnn 8:
https://developer.nvidia.com/compute/machine-learning/cudnn/secure/8.0.5/11.1_20201106/cudnn-11.1-linux-x64-v8.0.5.39.tgz

Install cudnn per:
https://askubuntu.com/questions/1230645/when-is-cuda-gonna-be-released-for-ubuntu-20-04

https://stackoverflow.com/questions/65273118/why-is-tensorflow-not-recognizing-my-gpu-after-conda-install

```
conda create -n kaggle_gpu4 python=3.7.6 
source activate kaggle_gpu4
conda install ipykernel
ipython kernel install --user --name=kaggle_gpu4
conda install tensorflow-gpu=2.1
pip install pandas
pip install keras-tuner 
pip uninstall tensorflow
pip install tensorflow-gpu==2.4.0
```
try 2:
```
conda create -n kaggle_gpu6 python=3.7.6 
source activate kaggle_gpu6
conda install ipykernel
ipython kernel install --user --name=kaggle_gpu6
pip install pandas
pip install keras-tuner 
pip install tensorflow-gpu
```
*shut down all other instances of this kernel, or else tensorflow will error *

- error maybe gcc or bazel need updating?
Process finished with exit code 132 (interrupted by signal 4: SIGILL)

pip install --user --force-reinstall --ignore-installed --no-binary :all: tensorflow-gpu


#### install tensorflow with gpu (old version)
https://askubuntu.com/questions/1230645/when-is-cuda-gonna-be-released-for-ubuntu-20-04 <br>
`sudo apt install python3-testresources`<br>
`conda install tensorflow-gpu` (for 2.4, Kaggle) OR `sudo pip3 install tensorflow-gpu==2.2.0 --user --ignore-installed` <br> 
`pip install keras-tuner`<br>
`pip install pandas`<br>
- shut down all other instances of this kernel, or else tensorflow will error 
- kaggle install: <br>
https://github.com/Kaggle/docker-python/blob/master/Dockerfile <br>
https://github.com/Kaggle/docker-python/blob/master/gpu.Dockerfile <br>