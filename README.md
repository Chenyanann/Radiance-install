# Introduction to install radiance on ubuntu 22.04

First, I am a relatively new user of Radiance and Ubuntu.
I have spent a lot of time and was finally able to install a working copy of Radiance. 
Below is a small guide to compile and install Radiance in Ubuntu 22.04. 
I would like to help newbies like me to get Radiance working on Ubuntu 22.04 with as little pain as possible.

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

Note: The '#' symbol means you need to enter root mode to compile, 
so it is recommended to turn off the password and enter **sudo -i** to enter root (root mode)

We need to download the required packages and their dependencies in order to compile using the synaptic package manager:
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

-- sudo apt install python3-pip

-- sudo apt-get install vim

-- python3 -m pip install numpy

-- sudo apt install tk

-- libc6-dev

-- libx11-dev

-- sudo apt-get install csh

-- sudo apt install gcc

-- sudo apt install g++

-- sudo apt-get install xorg

-- pip3 install libtiff

or type following in terminal:

-- sudo apt-get install tcsh g++ gcc tcl tk csh xorg libc6-dev libx11-dev

**Regardless of the installation method, please make sure to install the mentioned packages**

<summary><h2>Step 2: Install Radiance </h2></summary>

Prepare the Radiance for compiling

Create a directory in your HOME or /HOME/USER directory:  (I prefer to choose my directory /home/chen)

-- mkdir build

Change the working directory to it:

-- cd build

Download Radiance sources:

-- wget https://www.radiance-online.org/download-install/radiance-source-code/latest-release/rad5R3all.tar.gz

Unpack it:

-- tar -zxvf rad5R3all.tar.gz

Change the working directory to the source directory:

-- cd ray

<summary><h2>Step 3: Compiling Radiance </h2></summary>
This generates the necessary files and checks your system:

-- sudo tcsh makeall install

Give following answers to the queries generated by the install script:

Q1. Default editor [vi]?
Ans: y

Q2. Install to location usr/local/bin:
Ans: y

Q3. Read the license agreement ...
Ans: Scroll down using space bar. At the end it will ask:
q. Do you agree [n]:
Ans: y

Q4. Type of install? Choose from Sun, Sparc, Linux, etc.
Linux is listed at number 2
Ans: 2

Q5. Copy library files to 'usr/local/lib/ray'?
Ans: y

Q6. Install library files now?
Ans: y

Q7. Current rmake command is
#!bin/sh
....

Do you want to change it?
Ans: n

The programs and libraries are copied to usr/local/bin and usr/local/lib/ray respectively.

The environment variable Raypath is automatically set.

If all goes well you will have a working installation of Radiance.

**Note:**
----

1) In my case, the installation ended with the message "there were some errors",
As far as I was able to make out, this was because:

- libtiff was not compiled due to some compiler sanity check

- However, since latest libtiff was already downloaded and installed in
first Step in Ubuntu, this did not cause a problem.

2) Some binary files from installation directory:

i.e. /build/ray/src/px

like macbethcal, pcomb, pfilt, ra-bmp, ... ttyimage, etc.
were not automatically copied to the /usr/local/bin directory.

- So I manually copied the files using the nautilus file manager
as root by using the following command:

sudo nautilus

Note: copy the files whose icons are a rotated square with gears to the /usr/local/bin directory, 
if you don't know how to use 'nautilus' command, you can use linux command to copy this files one by one, for example:

-- cp -i /home/chen/build/ray/src/px/pcomb /usr/local/bin

3) For more details about the errors please refer to a file
named as config.log. You can search for this file from the desktop
menu:
Places--->
Search for files (with magnifying glass icon)

The config.log file in my case was located at:
home/chen/build/ray/src/px/tiff/config.log


Conclusion:
-----------

I hope that this guide is helpful. It has been written with the best of intentions. 
There may be errors, so I request advanced users to kindly review it and update the same.


References:
-----------

[1] http://www.radiance-online.org/pipermail/radiance-general/2008-February/004779.html

[2] https://radiance-general.radiance-online.narkive.com/K3zSnvpJ/installing-radiance-in-ubuntu-7-10-step-by-step-guide

[3] ?????????.??????????????????:Win10???Linux???????????????Radiance??????
