# external TPU

In the Robolab an external TPU is available, which can be used for mobile machine learning applications. 
In addition, an external GPU (<a href=https://github.com/IntelligentRoboticsLab/robolabws/blob/master/eGPU.md> eGPU.md</a>) and four workstations with good internal GPUs are available as rapid prototyping machines (<a href=https://github.com/IntelligentRoboticsLab/robolabws/blob/master/README.md>README.md</a>).
This external TPU is meant to be able to use pretrained models on your mobile device (iOS or Android), because coprocessors are typically not available on mobile devices.
The downside is that you have to do cross-development on your laptop and port your code than to the mobile device.

# Hardware Specifications

* Type: Coral - Google Edge TPU
* Cpu: none
* Memory: none 
* TPU for calculation: Global Unichip Corp
* interface: USB 3.1 (gen 1) Type-C socket

More details:
https://coral.withgoogle.com/products/accelerator/

# Interface

# Performance

Note the performance in <a href=https://coral.withgoogle.com/tutorials/edgetpu-faq/>Frequent Asked Questions</a>, where the external TPU boosted the performance of a desktop CPU with a factor 20x.


# Notes

When you first set up the Coral USB Accelerator, you can select whether to use the default or maximum clock frequency. The maximum clock frequency runs at 2x the default setting.

To change the setting later, you currently must uninstall the libedgetpu_*.so file, then rerun the install script, in which you'll be prompted to select the setting.
