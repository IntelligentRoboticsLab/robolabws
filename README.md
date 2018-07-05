# Intentions
The two workstation can be used for any computationally intense project or homework assignment but is mainly designed to be a rapid prototyping machine. This means that you can easily develop your software after which you offload it to some cloud provider. You can get a user account without sudo rights on this machines.

In addition, a external GPU station is available, which allows to accelerate the training on your own laptop when the laptop has no internal GPU. To be able to use an external GPU, your laptop needs at least a Thunderbolt interface. More details of this setup can be found in another document: eGPU.md.

To get a user account you can send an application to the following email address: `douwe@dutchnaoteam.nl` and make sure it includes the following information:

* Your full name and those of your partners (if applicable) 
* Education (AI, CS, etc..)
* Education level (Bachelor/Master)
* Honours Project (Yes/No)
* Project Description 
    * Abstract
    * Timeframe (when you expect to start and finish)
    * Required resources
    * Required software
    
When you need access to the robolab, contact A.Visser@uva.nl with the following information:
* studentnummer
* passnummer

# Important notice
Keep in mind that your home directory on the computer is public. To prevent any trouble, it is smart to make folders containing important keys or details private, or make your entire home directory private.

# Hardware Specifications
* Cpu: Intel E5-2640 v4 (10 cores/20 threads)
* Memory: 64 GB DDR4 
* GPU for calculation: NVidia 1080 Ti (12 GB)
* One computer has a Titan xp as a second GPU and the other computer has a NVIDIA GTX 470 as second GPU, mainly to serve the display. 

# Software
* NVidia driver 384
* cuda-9.0 (with cudnn 7.0.3)
* Tensorflow wheels are available for python 2 and 3. The python2 wheel is located at /home/robolab/tensorflow_pk_2/ and the python 3 wheel is located at /home/robolab/tensorflow_pk/
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

# Updates
To keep the machine safe and up to date, every first Tuesday of the month an update-upgrade will be performed. If this caused any troubles for you, inform the administrators.

