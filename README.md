# Introduction to install radiance on ubuntu 22.04

First, I am a relatively new user of Radiance and Ubuntu.I have spent a lot of time and was finally able to install a working copy of Radiance. Below is a small guide to compile and install Radiance in Ubuntu 22.04. I would like to help newbies like me to get Radiance working on Ubuntu with as little pain as possible.

I hope that someone finds it useful.


<summary><h2>Step 0: Download the required packages</h2></summary>

There may be others like me, so this small guide is intended for them.

We will install Radiance from source, but there are alternatives though like

1) change your distro or upgrade to **Ubuntu 22.04**

2) try intrepid (Ubuntu 22.04) packages by using backports

3) get live CD, jammy-desktop-amd64.iso (which uses Ubuntu 22.04)

OK, let's start the process to compile radiance from source package

<summary><h2>Step 1: Preview work</h2></summary>

To avoid entering a password every time you use the sudo command, we can turn it off. To do this

1. Open visudo by typing the command **sudo visudo** in the terminal;

2. Find **%sudo ALL=(ALL:ALL) ALL** and change this to **%sudo ALL=(ALL:ALL) NOPASSWD:ALL**

Note: The '#' symbol means you need to enter root mode to compile, so it is recommended to turn off the password and enter **sudo -i** to enter root (root mode)
We need to download the required packages and their dependencies in order to compile using the synaptic package manager:.
- pip
- vim
- tcsh
- numpy
- g++
- gcc
- tcl
- tk
- xorg
- libc6-dev
- libx11-dev

**Note: Install numpy before installing libtiff, otherwise an error will occur**
enter root mode, and type the command:
- sudo apt install python3-pip
- sudo apt-get install vim
- python3 -m pip install numpy
- sudo apt install tk
- libc6-dev
- libx11-dev
- sudo apt-get install csh
- sudo apt install gcc
- sudo apt install g++
- sudo apt-get install xorg
- pip3 install libtiff
or type following in terminal:
# sudo apt-get install tcsh g++ gcc tcl tk csh xorg libc6-dev libx11-dev

** Regardless of the installation method, please make sure to install the mentioned packages**

