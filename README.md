# FPGA nodes for ROS2


The ambition of this project is to develop open-source **ROS2 FPGA modules** which would act as **plug&play** ROS nodes. 

Imagine you could take a camera, plug it to the Ethernet router and you would have immediately available a ROS topic */your_camera/camera_info* and */your_camera/image_proc* where */your_camera/image_proc* topic would contain output of DNN classifying image pixels to road and off road. The DNN inference with your trained network would run on the FPGA embedded in the camera. You could then take this camera, and plug to other robot with different hardware and would still 

## Description

### ROS2 hardware nodes

One of the most exciting changes between ROS1 and ROS2 is the revamped communication. ROS2 incorporates DDS in its core for communication between the nodes. DDS is a widespread communication standard with years of development and deployment in many industrial applications. ROS2 does not have anymore a rosmaster and thus is distributed in the nature. Also, ROS2 can natively run on ARM processors. 

 This lowers the computation demands and allows to:
 - either create hw modules communicating using ROS interface,
 - or embed ROS2 directly in the modules.


### Why FPGAs?

FPGAs (= field-programmable gate arrays) were first introduced in 90s as a tool for prototyping electronics. FPGA integrates programmable logic blocks in an array; the logic blocks can act as a memory or logic function like AND or XOR. The blocks' i/o signals can be rerouted in a complex structures to create even a processor.

They, however, have become popular beyond prototyping electronics. For example, they are used for electronics in space probes since they allow over-the-air hardware updates--a very useful feature for probes which begin its mission years or even decades after the  electronics installation. FPGAs turned out to be a useful tool for accelerating image-processing algorithms and running DNN inference. In the latter, they are particularly interesting for robotics as they offer significantly lower power consumption compared to the graphic cards.

The recent trend is to build boards integrating an ARM processor with an FPGA chip which makes the boards selfcontained. This is exciting for the applications where networking is necessary, like our ROS modules. The ARM processor can be used to run the DDS communication. In fact, the ARM processor is even powerful enough to run ROS2.

### Model based design

FPGAs are typically programmed using VHDL. While learning VHDL syntax is easy, developing complicated data processing structures in VHDL can be time-demanding and complicated. Certainly, roboticists don't need such a skill. Here tools from Mathworks for code generation become handy. Simulink allows generate FPGA code and ARM code and even configures the interfaces. 

### Other efforts

This is not the first project trying to build HW nodes. In fact, ROS2 have been built with that in mind. For example, folks from Erle Robotics have a DARPA grant to develop ambitious H-ROS. H-ROS will use Power over Ethernet to plug-in&play sensors and actuators. Their effort is however not open and their business plan is focused on manufacturers who should be forced to be compliant with their standard and thus limited to their ecosystem of routers. 

## Development

1. First step is to develop a DDS Simulink module wrapper allowing ROS2 communication in Simulink. For v0.1 the wrapper should be able to publish/subscribe Int topic. 
2. Once the ROS nodes can discover the Int topic from the FPGA module,  that should be extended to Image topic. Image should be processed on the FPGA and published back.
3. Connect other sensors directly to the FPGA dev board, postprocess the data on the FPGA, and publish the data back.
4. Define typical interfaces for sensors and actuators. 
5. Build configurable Simulink block for the communication.

### How can you contribute? 

TBD



## Users

### Ambition

### Choosing FPGA

TBD

## Versions

### v0.0

- Project description in the readme


