# Force-based DS modulation

This ROS package contains the software implementation related to the work about motion and force generation
with dynamical systems: 

The practical experiments were performed with KUKA LWR IV+ robots.

# Installation

First, make sure that your ssh key are correctly set up. This would be needed for installing the dependencies

Go in the `src` directory of your catkin workspace and clone this package:
```sh
git clone https://github.com/walidAmanhoud/force_based_ds_modulation.git
```
Stay in the `src` directory and run the script *install_dependencies.sh*:
```sh
source force_based_ds_modulation/install_dependencies.sh
```
This script should install the package dependencies and compile everything

# Dependencies
The main dependencies are the following ones:

 - **ROS**: Robot operating system
 - **CMake**: Build system
 - **Eigen**: A library for linear algebra
 - **libsvm**: A library for Support Vector Machines (SVM)
 - **SVMGrad**: A ROS-package to evaluate SVM decision function and its derivatives
 - **kuka-lwr-ros**: A ROS-package to control the KUKA LWR IV+
 - **mocap_optitrack**: A ROS-package to work with the NaturalPoint Optitrack motion capture system
 - **net-ft-sensor**: A ROS-package to work with the ATI 6-axis force torque sensors
 - **sg_differentiation**: A ROS-package implementing Savitzky-Golay smoothing and differentiation
 - **utils**: A ROS-package implementing custom functions mainly for robot motion generation

Have a look to the _dependencies.rosintall_ file in the package directory to get the package dependencies' addresses.

# File hierarchy

The file system is divided in several subfolders:
 - `cfg`: contains _.cfg_ files used by dynamic reconfigure
 - `config`: contains _.yaml_ used by launch files
 - `data_grasping`: Contains the log files generated by the ObjectGrasping class 
 - `data_polishing`: Contains the log files generated by the SurfacePolishing class
 - `data_surface`: Contains the log and model files generated by the SurfaceLearning class
 - `data_workspace`: Contains the workspace model files generated for the KUKA LWR IV+. Please, refer to  https://github.com/sinamr66/SCA_data_construction to understand how these files can be generated
 - `cmake`: CMake FindXXX scripts
 - `include`: contains class header files
 - `launch`: contains _.launch_ files
 - `src`: contains class implentations and source files to instantiate them:
    - _SurfaceLearning_: A class used to learn the model of a surface
    - _SurfacePolishing_: A class used to perform a "circular" polishing on a surface with a KUKA LWR IV+ robot
    - _Workspace_: A class used to evaluate the reachable workspace of the KUKA LWR IV+ robot
    - _ObjectGrasping_: A class used to reach, grasp and manipulate an object with two KUKA LWR IV+ robots
    - _TwoRobotsTransform_: A class publishing the TF transform between the two KUKA LWR IV+ robots (used for the object       grasping task)

The `data_grasping`, `data_polishing`, and `data_surface` directories are generated automatically during the installation.

