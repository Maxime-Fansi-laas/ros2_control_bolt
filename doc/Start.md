# START
In the Start we will see 3 things :
-   How to have ros2 and ros2 control,
-   How to create a good workspace and Bolt with all there dependencies,
-   And how to do your first colcon build.


## 1 - First step, ROS 2 :

The `Robot Operating System` (ROS) is a set of `software libraries` and tools for building robot applications. From drivers to `state-of-the-art` algorithms, and with powerful developer tools, ROS has what we need for Bolt project. And it’s all `open source`.

ROS 2 is the big brother of ROS 1. He adapts the changes of robotics community since the start of ROS 1 and leveraging what is great about ROS 1 and improving what isn’t.


### 1) Download ROS2 :

- You need a local setup with `Ubuntu 20.04`.
- If you have one go to this link for [ROS 2 Foxy Installation](https://docs.ros.org/en/foxy/Installation.html)

### 2) Download ROS2 CONTROL :

`ROS2 CONTROL` is a framework for (real-time) control of robots. Its goal is to simplify integrating new hardware and overcome some drawbacks.

- Type that on your Terminal :

        sudo apt update
        sudo apt install ros-foxy-ros2-control
        sudo apt install ros-foxy-ros2-controllers


## 2 - Second step, Workspace :

You need to have a `clear workspace` to do some tests or find your files easily. Many different workspaces exist but for the rest of the tutorial you would be easier to use the same workspace name as me.

1) Having a `local workspace` is better (when you are in LAAS otherwise you dont need it):

        cd /users/local/<User_Name>

2) If the path doesn't exist `create it` :
    - Go to :

          cd /
          sudo mkdir -p users/local/<User_Name>
          cd users/local/
          sudo chown User_Name User_Name

3) Source your ROS2 and Create your `own Workspace` :

        source /opt/ros/foxy/setup.bash
        mkdir -p Bolt_ws/src
        cd Bolt_ws/src

4) Add the `Bolt project` (in the src file) (You need to have `git tool install`) :

        git clone --recursive https://github.com/stack-of-tasks/ros2_control_bolt.git

5) Add some `dependencies` of Bolt (in the src file) :

        git clone --recursive https://github.com/open-dynamic-robot-initiative/master-board.git
        git clone --recursive https://github.com/open-dynamic-robot-initiative/odri_control_interface.git
        git clone --recursive https://github.com/stack-of-tasks/ros2_hardware_interface_odri.git
        sudo apt install python3-sphinx python3-pybind11 ros-foxy-xacro



## 3 - Third step, Colcon Build

Every time you change something in your code you need to upload with a `colcon build` otherwise your updates won't be transmitted.

1) `Install Colcon` with these extension :

                sudo apt update
                sudo apt install python3-colcon-common-extensions

2) Go to the `Bolt_ws` workspace :

        cd ..
        
This command allows to go from the current directory to the previous one. Here, we go from `Bolt_ws/src` to `Bolt_ws/`

3) Do your first `Colcon Build` :

        colcon build
        
   We won't go into details here, but this command creates `install`, `log` and `build` folders. 

4) If everything installs properly you must come to this end when you do your first `colcon build` :

![Colcon Build](https://github.com/Benjamin-Amsellem/ros2_control_bolt/blob/master/ros2_control_bolt_tuto/pictures/Start_Bolt_1-R.png?raw=true "Colcon Build")

   These are the names of the packages that have been compiled.

5) To only `update a part` of your code you changed, you can do this :

        colcon build --packages-select ros2_hardware_interface_odri

   This example is only here for updating the package ros2_hardware_interface_odri


**Now you have all you need for the project and you know how to do Colcon Build**



### That's all for the first Tutorial on Bolt, I hope it could help you and go to the [next Tutorial for the next part](https://github.com/Maxime-Fansi-laas/ros2_control_bolt/blob/master/doc/Setup_Bold.md).
