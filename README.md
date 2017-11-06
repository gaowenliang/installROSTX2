# installROSTX2
Install Robot Operating System (ROS) on NVIDIA Jetson TX2

Right now, follow http://wiki.ros.org/Installation/Ubuntu is able to install the ROS on TX2. Or follow nwxt cmd:

Setup sources.lst

`sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`

Setup keys

`sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`

Installation

`sudo apt-get update`

`sudo apt-get install ros-kinetic-desktop -y`

Initialize rosdep

`sudo apt-get install python-rosdep -y`

`sudo rosdep init`

if fail on this step, try Certificates are messed up:

`sudo c_rehash /etc/ssl/certs` then do `sudo rosdep init`

To find available packages, use:

`rosdep update`

Environment Setup

`echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc`

`source ~/.bashrc`

Install rosinstall

`sudo apt-get install python-rosinstall -y`


 

The scripts will install Robot Operating System (ROS) on the NVIDIA Jetson TX2 development kit.

Tested on L4T 27.1

The script is based on the Ubuntu ARM install of ROS Kinetic: http://wiki.ros.org/kinetic/Installation/UbuntuARM

Maintainer of ARM builds for ROS is http://answers.ros.org/users/1034/ahendrix/

<strong>updateRepositories.sh</strong>
This is an optional step. Adds the repositories universe, multiverse, and restricted and then apt-get update. These repositories are in the standard 27.1 install, so probably not needed.

<strong>installROS.sh</strong>
Adds the ROS sources list, sets the keys and then loads ros-kinetic-ros-base. Edit this file to add other ROS packages for your installation. After loading, rosdep is initialized.

<strong>setupCatkinWorkspace.sh</strong>
Usage:

$ ./setupCatkinWorkspace.sh [optionalWorkspaceName]

where optionalWorkspaceName is the name of the workspace to be used. The default workspace name is catkin_ws. This script also sets up some ROS environment variables. Refer to the script for details.

