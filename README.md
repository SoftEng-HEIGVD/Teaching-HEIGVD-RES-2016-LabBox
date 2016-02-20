# Teaching-HEIGVD-RES-2016-LabBox

This repo hosts a Vagrant environment prepared for the students of the RES course taught at the HEIG-VD in Yverdon-les-Bains, Switzerland.

Following the instructions will give you a working environment, where you will get a linux virtual machine (with Virtual Box) with all the tools used in the labs: java, maven, node.js, docker and others.

## Requirements

1. **Install VirtualBox on your machine**. You can download the bits [here](https://www.virtualbox.org/wiki/Downloads).

2. **Install Vagrant on your machine**. You can download the bits [here](https://www.vagrantup.com/downloads.html). 

**WARNING** for linux users: do not install vagrant with `apt-get install`. The repos contain old versions, which have caused us lots of problems in the past!

## Setup procedure

1. Clone this repo on your machine. **WARNING for Windows users**: if you have accents or special characters in your name, you might have issues sooner or later if you work under your home directory. To avoid issues, we recommend that you clone the repos in directory directly under your main drive.

2. Move into the cloned repo and fire up vagrant with `vagrant up`. This will initiate a download of the base box (unless you have already used it in the past), so it will take some time (~15 minutes if you have a decent network connection).

3. Connect to your box with `vagrant ssh`. Understand that you are now on a linux terminal, in a virtual machine that is executed by VirtualBox. VirtualBox is running in headless mode, which means that you will not see the usual GUI.

Here is what it should look like in your terminal:

```
git clone git@github.com:SoftEng-HEIGVD/Teaching-HEIGVD-RES-2016-LabBox.git

```
