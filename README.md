# Machine Learning Machines

There are now nine workstations available in the robolab (L0.01) at LAB42.

# Intentions
The workstations can be used for any computationally intense project but is mainly designed to be a rapid prototyping machine. This means that you can easily develop your software after which you offload it to some cloud provider. You can get a user account without sudo rights on this machines.

To get a user account, please send a mail to `robolabws@gmail.com` with the following information:

* Your full name and those of your partners (if applicable)
* Education (AI, CS, etc..)
* Education level (Bachelor/Master)
* Honours Project (Yes/No)
* Project Description
    * Abstract
    * Timeframe (when you expect to start and finish)
    * Required resources
    * Required software
    * Required Ubuntu version
* If the use of a the desktop screen is important for the project at hand and for how long

If you need access to the robolab, please also add the following information:
* studentnummer
* passnummer

If any problems or questions come up, you can email to `robolabws@gmail.com`

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

The one Aurora-R11 computers has the following specifications:<br>
* Cpu: Intel Core i9 10900KF (10 cores/20 threads)
* Memory: 64 GB DDR4
* GPU for calculation: NVidia RTX 3090 (24 GB)

The ip for WS10 ends with .126<br>


# Software
* Tensorflow wheels are available for python 2 and 3. The python2 wheel is located at /home/robolab/tensorflow_pk_2/ and the python 3 wheel is located at /home/robolab/tensorflow_pk/ on workstation 1 and 2. Currently the wheels are Tensorflow version 1.4. When using the wheels to install tensorflow, you will get a version that is optimized for the CPU in the workstation and it will perform better than the version that is installed using pip.
* openCV 3 has also been compiled and is available on request.

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
The machines are located in the Robolab, room L0.01.

# Updates
To keep the machine safe and up to date, every first Tuesday of the month an update-upgrade and a restart will be performed. If this caused any troubles for you, inform the administrators.

# Guidelines
The following are rules that every user granted access to the workstation should follow:

* Always make sure to keep backups of your data - as the machines are heavily used and disk space is limited, disk cleanups will happen!
* Abusing the use of a desktop, thus clouding the GPU is penalising others who also need the GPU power, please check carefully whether your program is using what you expected it to use.
* Every user, should if possible, be present in room L0.01 when using the workstations. This makes it easier to coordinate the use of each workstation. When you are the only user of the workstation you could work from home.
* In the case of the unavailability of the room, one could still connect to the workstation via SSH connection with the appropriate credentials through the terminal or via SFTP connection in Nautilus or any file manager in Linux or through an IDE. Only one of the WSs can be reached from outside, from there you can jump to the other WSs. Ask Joey for the procedure.
* When using a notebook remotely on the workstation, always close after the work is finished, it frees spaces
* Always close all applications and log off if you're not using the workstation to free space on the GPU.
* When you're done with your project, your account will be blocked and your data will be removed.

# Work remotely with SSH

You can access your assigned machine (ws{number}) from the outside through the following procedure:

``ssh jumpbot@145.100.134.14 -i ~\.ssh\{your_ssh_key}``

From here you can "jump" to your specific machine:

``ssh {username}@ws{number}``

Alternatively, you can make a ssh config file:

``nano ~/.ssh/config``
```
Host jumpbot  
   HostName 145.100.134.14  
   User jumpbot  
   IdentityFile ~/.ssh/{your_ssh_key}
  
Host ws{number}
   Hostname wsnumber} 
   user {username}
ProxyJump jumpbot 
```
After saving the config, you can directly login with:
``ssh ws{number}``

# Tips
The following are handy commands, when one need to connect and be flexible while working with a SSH connection:
* Watch the usage of the GPU and which user is using it </br>
  ```watch -n 1 nvidia-smi```
* Use <a href="https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/"> tmux</a> to start a session on the workstation and be able to detach it so your session will keep alive until you kill the tmux server. For the person more familiar with tmux, this <a href="https://gist.github.com/MohamedAlaa/2961058"> cheatsheet </a> will come in handy. 
* To see which user is using all the resources, use the following command on the terminal</br>
``` htop ``` </br>
* Alternative text editor on the workstations besides *gedit* are <a href="https://www.jetbrains.com/help/pycharm/install-and-set-up-pycharm.html"> pycharm </a>, <a href="https://www.jetbrains.com/help/clion/install-and-set-up-product.html"> cLion </a> or <a href="http://docs.sublimetext.info/en/latest/getting_started/install.html"> sublime </a>. These editors are installable without admin rights. </br>
* Installing new packages for python is done by using the following command that do not requires admin rights </br>
``` pip install --user nameOfPackage ```
* Using the environment variable CUDA_VISIBLE_DEVICES, you can select which GPU your program uses. Use like this example to only use the second GPU in the computer:
```CUDA_VISIBLE_DEVICES=1 python3 myprogram.py```
