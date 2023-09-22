# Installing-Gazebo-and-ArduPilot-Plugin 
( Best Tested with Ubuntu 18 and Python2)

# Detailed Youtube Video Link

https://youtu.be/9cYW2FwJXg4


# Prerequisite
Recommended Ubuntu versions starting from 16.04 or 18.04 as those were the platform used for testing this approach. They are also known to be compatible with SITL.
This plugin can be used with or without ROS integration. In both case it is recommended to use Gazebo from the OSRF repository.




# GAZEBO 
Robot simulation is an essential tool in every roboticist's toolbox. A well-designed simulator makes it possible to rapidly test algorithms, design robots, perform regression testing, and train AI system using realistic scenarios. Gazebo offers the ability to accurately and efficiently simulate populations of robots in complex indoor and outdoor environments. Gazebo is free with a vibrant community.

for more infromation on gazebo checkout http://gazebosim.org/

# Installation

Ready your computer to accept software from http://packages.osrfoundation.org:

    sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'

    wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
    
    sudo apt update
    
    
The plugin we will be using works with gazebo versions 7 to 9. We recommend gazebo9 as the new development will append on this version. It isn’t available for older versions of Ubuntu though, so you may need to use an earlier version depending on your system.

    sudo apt install gazebo9 libgazebo9-dev

check the installation by launching Gazebo.
    
    gazebo --verbose
    
you will see world here and now you are ready to install ardupilot plugins.


# Plugin installation

We will be using khancyr plugin for the following exaplation. First clone it somewhere in your home directory. 

    git clone https://github.com/khancyr/ardupilot_gazebo
    
    cd ardupilot_gazebo
    
    mkdir build

    cd build

    cmake ..
    
    make -j4
    
    sudo make install
    
    
    
    echo 'source /usr/share/gazebo/setup.sh' >> ~/.bashrc


Setting path for models

    echo 'export GAZEBO_MODEL_PATH=~/ardupilot_gazebo/models' >> ~/.bashrc
    
    . ~/.bashrc
    
    
    
# Run Simulator    

    gazebo --verbose ~/ardupilot_gazebo/worlds/iris_arducopter_runway.world 
    
    
 
 # launch SITL 
 launch sitl in other terminal
 
     cd ~/ardupilot/ArduCopter/
     sim_vehicle.py -v ArduCopter -f gazebo-iris --console
     
     
If you have not installed the ardupilot stack then refer below link to install it

 https://github.com/punkypankaj/Installing-ArduPilot-directory/blob/main/docs.md
 
    
