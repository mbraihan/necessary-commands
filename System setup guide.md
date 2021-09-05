# Install NVIDIA driver, CUDA, cuDNN,openpose on Ubuntu 21.04

0. Pre-requisites
   Disabling nouveau driver id enabled
   ``` shell
   $ lsmod | grep nouveau
   $ sudo apt-get update
   $ sudo apt-get install build-essential
   $ sudo apt-get install cmake

   $ gcc --version
   $ cmake --version
   ```
1. Install NVIDIA driver
   Let's, detect the model of the GPU and recommended driver.
   ``` shell
   $ ubuntu-drivers devices
   ```
   Let's install the recommended driver
   ``` shell
   $ sudo ubuntu-drivers autoinstall
   $ sudo reboot
   ```
   View the installed NVIDIA info and uninstall the driver
   1. Check which drivers are installed in the system
   ``` shell
   sudo dpkg --list | grep nvidia-*
   ```
   2.Uninstall the NVIDIA driver
   ``` shell
    $ sudo apt-get --purge remove nvidia-*
    $ sudo apt-get --purge remove "*nvidia*"
2.  Install CUDA

    2.1. Clean up
    (a) Open a terminal window and type the following three commands to get rid of any NVIDIA/CUDA packages you may already have installed:
    ``` shell
    $ sudo rm /etc/apt/sources.list.d/cuda*
    $ sudo apt remove --autoremove nvidia-cuda-toolkit
    $ sudo apt remove --autoremove nvidia-*
    ```
    (b) Purge any remaining NVIDIA configuration files and the associated dependencies that they may have been installed with.

    ``` shell
    $ sudo apt-get purge nvidia*
    $ sudo apt-get autoremove
    $ sudo apt-get autoclean
    ```
    (c) Remove any existing CUDA folders you may have in /usr/local/
    ``` shell
    $ sudo rm -rf /usr/local/cuda*
    ```
    2.2 pre-Installations Actions
    Some actions must be taken before the CUDA Toolkit and Driver can be installed on Linux:

    1.Verify the system has a CUDA-capable GPU.
    ``` shell
    $ lspci | grep -i nvidia
    ```
    2.Verify the system is running a supported version of Linux.
    ```shell
    $ uname -m && cat /etc/*release
    ```
    3.Verify the system has gcc installed.
    ``` shell
    $ gcc --version
    ```
    4.Verify the system has the correct kernel headers and development packages installed.
    ``` shell
    $ uname -r
    ```
    5.Download the NVIDIA CUDA Toolkit: [CUDA](https://developer.nvidia.com/cuda-downloads)
    ``` shell
    $ wget https://developer.download.nvidia.com/compute/cuda/11.4.1/local_installers/cuda_11.4.1_470.57.02_linux.run
    $ sudo sh cuda_11.4.1_470.57.02_linux.run
    ```
    Add environemental variables
    ``` shell
    $ sudo vim ~/.bashrc
    ```
    Add the following environment variables to ~/.bashrc at the end of the file and save and exit.
    ``` shell
    export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
    export CUDA_HOME=/usr/local/cuda

    or
    export PATH=/usr/local/cuda-11.4/bin:$PATH
    export LD_LIBRARY_PATH=/usr/local/cuda-11.4/lib64:$LD_LIBRARY_PATH
    export CUDA_HOME=/usr/local/cuda

    export PATH=/usr/local/cuda-11.4/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-11.4/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
    export CUDA_HOME=/usr/local/cuda
    or

    echo 'export PATH=/usr/local/cuda-11.4/bin:$PATH' >> ~/.bashrc
    echo  'export LD_LIBRARY_PATH=/usr/local/cuda/lib64' >> ~/.bashrc
    ```
    You can check this by doing a
    ``` shell
    $ ls -l /usr/local/cuda
    ```
    Save & activate change
    ``` shell
    $ source ~/.bashrc
    ```