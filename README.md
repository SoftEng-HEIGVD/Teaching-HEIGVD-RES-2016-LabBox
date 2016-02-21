# Teaching-HEIGVD-RES-2016-LabBox

This repo hosts a Vagrant environment prepared for the students of the RES course taught at the HEIG-VD in Yverdon-les-Bains, Switzerland.

Following the instructions will give you a working environment, where you will get a linux virtual machine (with Virtual Box) with all the tools used in the labs: java, maven, node.js, docker and others.

## Requirements

1. **Install VirtualBox on your machine**. You can download the bits [here](https://www.virtualbox.org/wiki/Downloads).

2. **Install Vagrant on your machine**. You can download the bits [here](https://www.vagrantup.com/downloads.html). 


**WARNING** for linux users : 

1. For **Debian** and derivative: do not install vagrant with `apt-get install`. The repos contain old versions, which have caused us lots of problems in the past!

2. For **Fedora**: vagrant should be installed via dnf or yum. Fedora has up to date packages in its repositories. VirtualBox can also be found in [rpmfusion.org](http://rpmfusion.org/Configuration) repositories, with an as up-to-date and better integration than on the official site. Once enabled, you only have to `sudo dnf install VirtualBox vagrant`

## Setup procedure

1. Clone this repo on your machine. **WARNING for Windows users**: if you have accents or special characters in your name, you might have issues sooner or later if you work under your home directory. To avoid issues, we recommend that you clone the repos in directory directly under your main drive.

2. Move into the cloned repo and fire up vagrant with `vagrant up`. This will initiate a download of the base box (unless you have already used it in the past), so it will take some time (~15 minutes if you have a decent network connection).

3. Connect to your box with `vagrant ssh`. Understand that you are now on a linux terminal, in a virtual machine that is executed by VirtualBox. VirtualBox is running in headless mode, which means that you will not see the usual GUI.

4. When you are connected to your box, you can run the pre-installed software. For instance, we have installed a java 8 environment, so you can use the `java` command.

5. You can exit your box at any time and use `vagrant halt` to ask VirtualBox to stop the VM. Later on, you can restart it with `vagrant up`.


Here is what it should look like in your terminal:

```
your-OS $ git clone git@github.com:SoftEng-HEIGVD/Teaching-HEIGVD-RES-2016-LabBox.git
your-OS $ cd Teaching-HEIGVD-RES-2016-LabBox/
your-OS $ vagrant up
your-OS $ vagrant ssh

vagrant@RES $ java -version
vagrant@RES $ exit

your-OS $ vagrant status
your-OS $ vagrant halt
```

## Setup your GitHub environment

We will use GitHub. A lot. So the very first thing that you want to do is to setup your user name and email. This is crucial, because you don't want to appear as "vagrant" in the commit history and we will need you real identify. There are two commands to type, see [here](https://help.github.com/articles/set-up-git/).

You then want to setup your ssh key so that you can authenticate yourself when cloning repos. The instructions are available on GitHub. 


 * Step 1 is described [here](https://help.github.com/articles/generating-a-new-ssh-key/#platform-linuvx).
  
 * Step 2 is [here](https://help.github.com/articles/adding-a-new-ssh-key-to-the-ssh-agent/#platform-linux). 
 
 * Step 3 is described [here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/#platform-linux)

You should (also) do that within the box (after doing a `vagrant ssh`) if you want to use git commands there, which we strongly recommend.

You can test your setup by cloning any repo using the ssh protocol.

## How is the file system structured and where should I clone other (lab) repos?

When you use Vagrant and do a `vagrant up`, the directory containing the `Vagrantfile` will be mounted in the VM and will be accessible at `/vagrant`. This means that the files under the `RES` directory can be accessed both from your host computer and from the VM. This is the case of the test file named `whereAmI.md` that you can play with:

```
your-OS $ ls -l ./RES/whereAmI.md
-rw-r--r--  1 admin  wheel  187 20 fév 10:48 ./RES/whereAmI.md

your-OS $ vagrant ssh

vagrant@RES $ ls -l /vagrant/RES/whereAmI.md
-rw-r--r-- 1 vagrant vagrant 187 Feb 20 09:48 /vagrant/RES/whereAmI.md
```

That's pretty useful and during the semester, you could use the following strategy to manage your git repo clones:

1. You will  often start by forking a source repo on GitHub, to have your own version of it (so that you can push your commits).

2. You will then connect to your box with `vagrant ssh` and do a `cd /vagrant/RES/repos`.

3. From there, you will clone your repo fork, using `git clone git@github.com:SoftEng-HEIGVD/XXX`. This means that the files (Java source files, scripts, etc.) will be available both in the VM and on your host.

4. Think about Java projects: it means that you will be able to use your IDE (we recommend Netbeans) on your host, edit the files, build the software, use the debugger, etc. But it also means that you will be able to build and run the software within the VM, in the command line (using maven).

Why is this important? We have an automated procedure to automatically test and grade some of the labs. If you do the final build and test in the VM, you will avoid issues caused by different operating systems (Windows vs Mac OS vs Linux). We will get back to these points in due time, but keep in mind that you have 2 ways to interact with the files.

![image](./diagrams/file-system-layout.png)
