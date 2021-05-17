# Machine Learning Machines

There are now ten workstations available: four in the robolab (C3.165) and six in the blue-student lab (C2.115 and C2.116).

# Intentions
The workstations can be used for any computationally intense project but is mainly designed to be a rapid prototyping machine. This means that you can easily develop your software after which you offload it to some cloud provider. You can get a user account without sudo rights on this machines.

In addition, a external GPU station is available, which allows to accelerate the training on your own laptop when the laptop has no internal GPU. To be able to use an external GPU, your laptop needs at least a Thunderbolt interface. More details of this setup can be found in another document: <a href=https://github.com/IntelligentRoboticsLab/robolabws/blob/master/eGPU.md> eGPU.md</a>. For mobile applications an external TPU is availabe (<a href=https://github.com/IntelligentRoboticsLab/robolabws/blob/master/eTPU.md>eTPU.md</a>) 

To get a user account, please fill in the following form: https://docs.google.com/forms/d/17g55QFfQvWaMBd_pTkS5fbABbB_1nxvXvbQvaZgeznc/edit 
This form will ask the following details:

* Your full name and those of your partners (if applicable)
* Education (AI, CS, etc..)
* Education level (Bachelor/Master)
* Honours Project (Yes/No)
* Project Description
    * Abstract
    * Timeframe (when you expect to start and finish)
    * Required resources
    * Required software  
* If the use of a the desktop screen is important for the project at hand and for how long

When you need access to the robolab, contact `A.Visser@uva.nl` with the following information:
* studentnummer
* passnummer

If any problems or questions come up, you can email to `robolabws@gmail.com` to email the admins.

# Important notice
Keep in mind that your home directory on the computer is public. To prevent any trouble, it is smart to make folders containing important keys or details private, or make your entire home directory private.

# Hardware Specifications

The two CoolerMaster computers have the following specifications:<br>
RobolabWS 1 (IP ends with .70):
* Cpu: Intel E5-2640 v4 (10 cores/20 threads)
* Memory: 64 GB DDR4
* GPU for calculation: NVidia 1080 Ti (12 GB) and NVidia Titan XP(12GB) with CUDA 9.0 and driver 384

RobolabWS 2 (IP ends with .74):
* Cpu: Intel E5-2640 v4 (10 cores/20 threads)
* Memory: 64 GB DDR4
* GPU for calculation: NVidia 1080 Ti (12 GB) and NVidia GTX 1080 (8GB) with CUDA 9.0 and driver 384

The two Aurora-R7 computers have the following specifications:<br>
robolabWS 3(IP ends with .107):
* Cpu: Intel Core i7 8700 (6 cores/12 threads)
* Memory: 64 GB DDR4
* GPU for calculation: NVidia 2080 Ti (11 GB), NVidia Titan V(12GB) with CUDA 9 and 10 and driver 415

robolabWS 4(ip ends with .108):
* Cpu: Intel Core i7 8700 (6 cores/12 threads)
* Memory: 64 GB DDR4
* GPU for calculation: NVidia 2080 Ti (11 GB) with CUDA 10 and driver 415

The four Aurora-R9 computers have the following specifications:<br>
* Cpu: Intel Core i7 9700 (8 cores/16 threads)
* Memory: 64 GB DDR4
* GPU for calculation: NVidia 2080 Ti (11 GB) with CUDA 10 and driver 415

The ip for WS5 ends with .204<br>
The ip for WS6 ends with .207<br>
The ip for WS7 ends with .206<br>
The ip for WS8 ends with .205<br>

The two Aurora-R11 computers have the following specifications:<br>
* Cpu: Intel Core i9 10900KF (10 cores/20 threads)
* Memory: 64 GB DDR4
* GPU for calculation: NVidia RTX 3090 (24 GB)

The ip for WS9 ends with 127<br>
The ip for WS10 ends with .126<br>


# Software
* The workstations are running Ubuntu 18.04.4 LTS
* Tensorflow wheels are available for python 2 and 3. The python2 wheel is located at /home/robolab/tensorflow_pk_2/ and the python 3 wheel is located at /home/robolab/tensorflow_pk/ on workstation 1 and 2. Currently the wheels are Tensorflow version 1.4. When using the wheels to install tensorflow, you will get a version that is optimized for the CPU in the workstation and it will perform better than the version that is installed using pip.
* openCV 3 has also been compiled and is available on request.

The on request software will soon be moved to a folder where it is accessible to all users of the machine.

To add precompiled software (for instance cuda) to your own environment add the following lines to your `~/.bashrc` file:

For libraries:
```
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/cuda-9.0/lib64
```

For executables:
```
export PATH=${PATH}:/usr/local/cuda/bin
```
# Location
The machines are located in the Robolab, room C3.165.
RobolabWS 1 and 3 are located in the Robolab, room C3.165 and RobolabWS 2 and 4 are located in C2.115.
RobolabWS 5,6,7 and 8 are located at the blue student lab in C2.116. RobolabWS 9 and 10 are located in the Robolab 

# Updates
To keep the machine safe and up to date, every first Tuesday of the month an update-upgrade and a restart will be performed. If this caused any troubles for you, inform the administrators.

# Guidelines
The following are rules that every user granted access to the workstation should follow:

* Every user should be member of the slack channel : https://robolabws.slack.com/ and communicate through the channel on which you have been assigned.
* Please help others in real life or on Slack , channel #daretoask, with problems if you know how to solve them. If you have a problem, see if you can ask someone or ask in the Slack question channel #daretoask. 
* Abusing the use of a desktop, thus clouding the GPU is penalising others who also need the GPU power, please check carefully whether your program is using what you expected it to use.
* Send an update in the Slack channel of your workstation when you'll be using a GPU, indicating the time span, which GPU will be used (if relevant) and how long the process will approximately run.
* Every user, should if possible, be present in room C3.165 when using the workstations. Exceptions is when the room is used for teaching purposes.
* In the case of the unavailability of the room, one could still connect to the workstation via SSH connection with the appropriate credentials through the terminal or via SFTP connection in Nautilus or any file manager in Linux or through an IDE
* When using a notebook remotely on the workstation, always close after the work is finished, it frees spaces
* Always close all applications and log off if you're not using the workstation to free space on the GPU.
* When you're done with your project, your account will be blocked. You will then receive a notification of the admin about the termination of your access to the Workstation.

# Tips
The following are handy commands, when one need to connect and be flexible while working with a SSH connection:
* Start a vpn-connection to get access to the UvA network
* Connecting to the workstation </br>
  ```ssh user@ipWorkStation``` </br>
  password: userPassWord
* Copying file to local machine to remote </br>
  ``` scp [file/dir -r] user@ipWorkStation:[pathToWorkstationFile]``` </br>
  password: userPassword </br>
* Porting local changes on port XXXX to remote YYYY </br>
  ``` ssh -N -f -L localhost:YYYY:localhost:XXXX user@ipWorkStation ```</br>
  For example, porting local changes on port 7865 to remote 8888 </br>
  ``` ssh -N -f -L localhost:8888:localhost:7865 user@ipWorkStation ```</br>
  ``` jupyter notebook --port=7865 ```
* Connecting to tensorboard remotely </br>
  ```ssh -L 18888:127.0.0.1:8888 user@ipWorkStation ``` </br>
  Serve locally to browser: ```http://127.0.0.1:18888/ ``` </br>
* Watch the usage of the GPU and which user is using it </br>
  ```watch -n 1 nvidia-smi```
* Connecting remotely through Nautilus </br>
  * Open Nautilus locally and select connect to server </br>
  * Set as server address: ```stfp://ipWorkStation/home/user```
* Use <a href="https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/"> tmux</a> to start a session on the workstation and be able to detach it so your session will keep alive until you kill the tmux server. For the person more familiar with tmux, this <a href="https://gist.github.com/MohamedAlaa/2961058"> cheatsheet </a> will come in handy. 
* To see which user is using all the resources, use the following command on the terminal</br>
``` htop ``` </br>
* Alternative text editor on the workstations besides *gedit* are <a href="https://www.jetbrains.com/help/pycharm/install-and-set-up-pycharm.html"> pycharm </a>, <a href="https://www.jetbrains.com/help/clion/install-and-set-up-product.html"> cLion </a> or <a href="http://docs.sublimetext.info/en/latest/getting_started/install.html"> sublime </a>. These editors are installable without admin rights. </br>
* Installing new packages for python is done by using the following command that do not requires admin rights </br>
``` pip install --user nameOfPackage ```
* Using the environment variable CUDA_VISIBLE_DEVICES, you can select which GPU your program uses. Use like this example to only use the second GPU in the computer:
```CUDA_VISIBLE_DEVICES=1 python3 myprogram.py```
