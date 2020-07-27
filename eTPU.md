# external VPU and TPU

In the Robolab two types of external VPU/TPUs are available, which can be used for mobile machine learning applications. 
In addition, an external GPU (<a href=https://github.com/IntelligentRoboticsLab/robolabws/blob/master/eGPU.md> eGPU.md</a>) and four workstations with good internal GPUs are available as rapid prototyping machines (<a href=https://github.com/IntelligentRoboticsLab/robolabws/blob/master/README.md>README.md</a>).
This external TPU is meant to be able to use pretrained models on your mobile device (iOS or Android), because coprocessors are typically not available on mobile devices.
The downside is that you have to do cross-development on your laptop and port your code than to the mobile device.

# VPU Hardware Specifications

* Type: Intel® Movidius™ Myriad™ X Vision Processing Unit (VPU)
* Cpu: none
* Memory: none 
* VPU for calculation: Myriad™ X MA2480 - 16 SHAVE cores
* interface: USB 3.0 Type-A socket

More details:
https://software.intel.com/content/www/us/en/develop/hardware/neural-compute-stick.html

# VPU Interface

https://docs.openvinotoolkit.org/latest/openvino_docs_install_guides_installing_openvino_raspbian.html

# VPU Tutorials

https://software.intel.com/content/www/us/en/develop/articles/get-started-with-neural-compute-stick.html

# TPU Hardware Specifications

* Type: Coral - Google Edge TPU
* Cpu: none
* Memory: none 
* TPU for calculation: Global Unichip Corp
* interface: USB 3.1 (gen 1) Type-C socket

More details:
https://coral.withgoogle.com/products/accelerator/

# TPU Interface

https://coral.withgoogle.com/tutorials/accelerator/#setup-for-linux-or-raspberry-pi

https://www.tensorflow.org/lite

https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite

# TPU Tutorials

https://www.tensorflow.org/guide/using_tpu

https://coral.withgoogle.com/tutorials/edgetpu-retrain-classification/

https://coral.withgoogle.com/tutorials/edgetpu-retrain-classification-ondevice/

# TPU Performance

Note the performance in <a href=https://coral.withgoogle.com/tutorials/edgetpu-faq/>Frequent Asked Questions</a>, where the external TPU boosted the performance of a desktop CPU with a factor 20x.


# Notes

When you first set up the Coral USB Accelerator, you can select whether to use the default or maximum clock frequency. The maximum clock frequency runs at 2x the default setting.

To change the setting later, you currently must uninstall the libedgetpu_*.so file, then rerun the install script, in which you'll be prompted to select the setting.
