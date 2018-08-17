# external GPU

In the Robolab an external GPU is available, which can be used for machine learning applications. In addition, two workstations with good internal GPUs are available as rapid prototyping machines. Those machines are described in another document (README.md). The benefit of an external GPU is that you can use your own laptop, the downside is that your laptop needs at least a Tunderbolt interface and that you have to some additional configuration.

# Hardware Specifications

* Type: Razer Core v2
* Cpu: none
* Memory: none 
* GPU for calculation: Nvidia Titan Xp
* interface: Thunderbolt 3

More details:
https://www.razerzone.com/gaming-systems/razer-core-v2

# Interface

The Razor Core has an 40Gbps Thunderbolt 3 cable. Physically it is an USB-C interface, but not every USB-C port is an Thunderbolt port.
A Thunderbolt port can be recognized with a lighting symbol. Inside your laptop the Thunderbolt port is connected with the  PCIe 3.0 lanes. If your laptop connects 4 PCIe lanes, you can make use of the full 40Gbps.

# macOS Software

Older Macs typically have a Thunderbolt 2 interface (physically a mini-display port). With the eGPU there is a Thunderbolt 2 to 3 converter available, together with a Thunderbolt 2 cable. That being said, Apple disabled eGPU over Thunderbolt 1 and 2 with macOS 10.13.4 and Nvidia GPU's are not officially supported. There are [ways to work around this](https://github.com/mayankk2308/purge-wrangler), but your mileage may vary.

Apple recommends as an alternative eGPU the [Blackmagic eGPU](https://support.apple.com/en-us/HT208544), but the AMD GPU inside cannot be upgraded. An alternative (upgradable) configuration could be a [Razer Core X with a Radeon Vega 64 ](https://9to5mac.com/2018/08/02/2018-macbook-pro-amd-vega-64-egpu-video/). Yet, the pre-requisite for these AMD alternatives  is that you can [port your Machine Learning project to an AMD Radeon GPU](https://instinct.radeon.com/en/6-deep-learning-projects-amd-radeon-instinct/).

# Ubuntu Software

Because a Thunderbolt provides a lot of access to your computer, as it supports protocols as PCIe 3.0, DisplayPort 1.2 and USB 3.1 (giving access to both input/output devices and storage). Access to your Ubuntu laptop have to be autorized, which can be checked with the command 'cat /sys/bus/thunderbolt/devices/0-103/authorized'. If this returns 0, access can be granted with the command 'sudo tbtadm approve-all'. The tool tbtadm can be installed with the command 'sudo apt-get install thunderbolt-tools' for Ubuntu 18.04 (or higher), or installed from [source code provided by Intel](https://github.com/intel/thunderbolt-software-user-space).

You can check if your external GPU is accessible with the command 'lspci | grep -i nvidia'. After that, follow the instructions of [the CUDA installation guide](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#abstract).

Tested the Titan Xp with the Matlab Parallel Computing Toolbox. In principle, if you can run any CUDA code on the card then so can MATLAB. MATLAB directly interfaces with the CUDA driver, it seems that it is not needed that the CUDA toolkit is installed. In practice the CUDA toolkit was already installed. The Titan Xp is detected by Matlab (gpuDeviceCount returns 1), and with but the command 'd = gpuDevice' more details about the GPU could be inspected. Executed the [MATLAB GPU benchmarking code](https://nl.mathworks.com/help/distcomp/examples/benchmarking-a-b-on-the-gpu.html), and the Titan Xp showed a speedup of 20.7x for a Single and 4.7x for a Double precision operation, compared to computing this with the CPU.

Installing the CUDA framework allows to inspect the load of the eGPU with command 'nvidia-smi'. Pure CUDA calculations work out of the box, for visualization on an external device CUDA has to have access to the external display.

# Windows10 Software

Once the Thunderbolt cable is connected to your Windows laptop, Windows will automatically install the device software (PCI-drivers, VGA-display, etc). The drivers for the display adapters are recent, yet not the latest. Downloading the latest drivers from Nvidia should in principal solve this, yet the Nvidia-install packages fails to detect the external GPU during the compatibility check, without an option to proceed on own risk (and without further notice).

The CUDA framework has this option to proceed without a compatible GPU. Yet, care has to be taken for the selection of the correct version of the CUDA framework (which is GPU dependent).

Note that it is wise to dismount the GPU before you disconnect the Thunderbolt cable. Dismounting can be done via the Nvidia GPU Activity window on the taskbar, which can also be used to check which programs are currently running on the GPU.

# Location
The machine is located in the Robolab, room C3.165.

When you need access to the robolab, contact `A.Visser@uva.nl` with the following information:

* studentnummer
* passnummer

# Reservations

When you need an eGPU, you can send an reservation to the following email address: `robolabws@gmail.com` and make sure it includes the following information:
* Your full name and those of your partners (if applicable)
* Education (AI, CS, etc..)
* Education level (Bachelor/Master)
* Honours Project (Yes/No)
* Project Description 
  * Abstract
  * Timeframe (when you expect to start and finish)
  * Required resources
  * Required software
  
 # Older GPUs
 
 Before the Titan XP arrived, the Razer Core v2 was tested with an older GPU:
  
  * Tesla C2050

The Tesla C2050 is of the Fermi architecture, compute capability 2.0, which means that CUDA until 8.0 is supported. 
Actually, the Windows driver is from June 2015, which supports CUDA until 7.5. Unfortunately, CUDA is not backwards compatible, so deviceQuery (in CUDA Samples\v9.2\1_Utilities) reports that the CUDA driver version is unsufficient for the CUDA runtime version. 

Luckely, Nvidia has [a Toolbox archive](https://developer.nvidia.com/cuda-toolkit-archive), including CUDA 7.5. Yet, the CUDA-toolkit has to installed on top C++ compiler, which in this case is Visual Studio 2013, which has to be installed BEFORE Cuda, so that the installer could augment visual studio with the correct v7.5.props definitions in its CustomBuild directories. Note that CUDA is sensitive on the version of Visual Studio, CUDA 7.5 cannot be build with Visual Studio 2015 or 2017. Visual Studio 2013 can be downloaded for free from http://my.visualstudio.com/.

With CUDA 7.5 still not all CUDA functionality could be used. Programs which use both CUDA and OpenGL context fail, because no OpenGL display is available on the external GPU. Yet, all matrix calculation work fine, it only goes wrong when you also like to see the visualisations. Best test on CUDA and OpenGL is recursiveGaussian (in CUDA Samples\v9.2\3_Imaging), which gracely falls back to benchmark when no OpenGL display is found.

Also tested the Tesla C2050 with the Matlab Parallel Computing Toolbox. In principle, if you can run any CUDA code on the card then so can MATLAB. MATLAB directly interfaces with the CUDA driver, the cuda-toolkit is not needed to be installed. In practice the Tesla C2050 is detected by Matlab (gpuDeviceCount returns 1), but using more advanced functionality (such as the  trainNetwork function of [Matlab's Deep Learning Toolbox](https://nl.mathworks.com/help/nnet/ug/deep-learning-with-big-data-on-gpus-and-in-parallel.html) fails on the CUDA version (at least CUDA 9.1 for R2018b). So for all functionality of the Parallel Computing Toolbox a NVidia card with at least a compute capability of 3.0 is needed (such as the Titan Xp donated by [NVIDIA](https://developer.nvidia.com/academic_gpu_seeding), which has the Pascal architecture with [a compute capability of 6.1](https://en.wikipedia.org/wiki/CUDA), which supports CUDA version 9.2). 
