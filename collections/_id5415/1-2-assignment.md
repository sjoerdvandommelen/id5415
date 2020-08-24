---
layout: course-page
title: "Assignment 1"
permalink: /module1/assignment
description: "Prototyping Connected Product - Assignment 1"
assignment-id: 1
assignment-of: id5415-1
introduction: Assignments is where the prototyping happens. In this firstassignment, you will set up a Raspberry Pi as a connected home hub to control connected light bulbs. We will walk you through the different steps while exploring the purpose of each component, incrementally drawing an product architecture.
prog_environment: Raspberry Pi
design: Architecture
code_management: Logs
computational_concepts: Data
---


---

* Do not remove this line (it will not be displayed)
{:toc}

---

# Step 1: A cloud

We will see in module 5 the concepts of cloud and web services. For now, we will assume that we need something on the Internet that helps us collect and visualise data.

Today there are plenty of such cloud services as it is a core component of the IoT technology stack.

In this course, we will rely on a set of tools that we developed at IDE to keep control of the functionalities and the data.

Here is a little tour:

TODO Video tour Bucket

Throughout the course, we will rely on these tools to collect and visualise data, but also to check the status of our 'Things' on the Internet.

## Task 1.1 Create a DCD Lab account

* connect to Bucket: https://dwd.tudelft.nl/bucket

* Sign in / Sign Up, OAuth2? 

Similar to your TU Delft account, all our tools are accessible via a single account from our Lab.

Sign up

Screen shot

## Task 1.2 Create a Raspberry Pi Thing

Once you log into Bucket, the dashboard shows an empty page with a form to create a Thing.

Following the phrasing of the Internet of Things, we've adopted this terminology to represent any physical or virtual entity that connect to the Internet and generate data.

Let's create a Thing for our Raspberry Pi, this little computer as part of the prototyping kit. Type in a name and a description, and select the type 'Raspberry Pi'.

Screenshot

Many input fields appear. As setting up a Raspberry Pi in a proper way can be cumbersome, Bucket will use this information to prepare a secured image for you ready to use.

Let's walk through these input fields and their purpose. Keep in mind that we do not store any of this information. We blend it into a Raspberry Pi image that only you, owner of the Thing you are creating, can download through a secured connection. 

The first section is about restricting the access to your Raspberry Pi. As you will store network information on your Raspberry Pi, it is essential to set it up in a way that prevent others to access it.

The second section is about connecting to the network. Eduroam is an enterprise grade network which requires several challenging intervention on the Raspberry Pi system. Filling in your NetId and password, we make sure that your Raspberry Pi can automatically connect to Eduroam and manage your credential properly. We conveniently provide a similar function for your home network.

Once you are down, click 'Create'. The page should update with your newly created Thing. However, it will take a 'long' time to generate your image. You can see a status indicator which will turn into a 'Download' button when your image is ready.

You can proceed to the next step while waiting for your Raspberry Pi image to be ready.

**What did we achieved?** 

* We have a cloud account enabling us to manage the data of our prototype. 
* We launch the generation of a ready-to-use system for the Raspberry Pi.

# Step 2: Four Key Development Tools

No worry, we will not start coding before the next module! However, we need a several tools in order to interact with the connected light bulb of the prototyping kit. Let's take this opportunity to introduce and install the tools we will use throughout the course.

## Task 2.1: Installing a Version Control System (VCS)

The first tool is Git, a Version Control System (VCS). A VCS facilitate the management of and the collaboration around a piece of code. We will cover Git and its purpose for prototyping connected products in the next module. For now, its installation (especially on Windows) helps us automatically set up an development environment.

Download and install Git from the [official website](https://git-scm.com/download). On Mac you might go for the Binary installer option.

## Task 2.2: Installing an Integrated Development Environment (IDE)

The next step is editing and executing code. Developers do this in an Integrated Development Environment (IDE), which simply is a text editor with convenience of code editing and execution. For this course, we will choose Visual Studio Code (or VS Code) which brings all the necessary functionalities without being overlly complicated.

Download and install VS Code from the [official website](https://code.visualstudio.com/).

Create a folder on your computer to store the files for this course. Open VS Code and click the top menu File > Open ... to open your your course folder. Let's take a little tour of the IDE.

* The left panel relates to the management of your files with from the top: 1. the tree of your project files 2. searching into your project files 3. managing your file with Git. This is the whole menu of Module 2;
* The bottom panel relates to the execution of code. We will especially look at the Terminal tab in the next task.

TODO screen shot with arrows

## Task 2.3: Basics of a Command-line Interpreter (CLI)

A Command-Line Interpreter or CLI is no tool for one project but rather for your entire digital prototyping life! In the software jargon, you will hear about 'Unix shell', 'Console', 'Terminal' or 'Command Prompt'. Whether it is the software itself or the language that it relies on, all of them refer to this black window full of scary lines. You write text, press enter, and it interpretes this text as a command (e.g. create a directory, open an application). Why would we use this primitive text-based interaction instead of clicking on graphical buttons (so called 'Graphical User Interface' or GUI)? When prototyping you are developing technologies and playing with cutting edge ones, mainy of which simply do not have GUIs. 

### Task 2.3.1 Setting up in VS Code

To find the Terminal in VS Code, go to View > Terminal. It opens a tab in the bottom panel. In this course we will use Unix shell as command line language which comes in different flavor, the most common being bash and zsh. On the top right corner of the Terminal, a drop down menu give you several options.

On Windows, the installation of Git should have install bash, **you must select bash instead of Power Shell.**

TODO screen shot with arrows

Each command line start with your username @ your machine name. Then, the current folder is shown

### Task 2.3.2 Basic commands

To execute a command simply type it, and press the ENTER key. Let's MaKe a DIRectory named 'test' with the command 'mkdir':

```bash
mkdir test
```

The new folder should appear in your file tree in the left panel. 'ls' is the command to list files and directories. Type ls followed by ENTER:

```bash
ls
```

Your test folder should appear as a result of this command.

TODO screenshot ls result

Most commands come with a manual, available with the command 'man'. Let's explore the option of the ls command.

```bash
man ls
```

TODO screenshot man

You can see a long list of option, starting with a dash '-'. These options can be combined together. For instance you will note -G for coloring the result and -l for the long and detailed result. To quit the manual, press 'q'. Now we can try:

```bash
ls -Gl
```

TODO screenshot

In the terminal, everything relates to where you are in the file tree, i.e. in which folder you are in. With the command 'cd' you can 'change directory' to navigate this tree. The 'path' is the chain of directories to reach your targeted file or directory.

```bash
cd test
```

You entered 'test' folder, you can notice the command line is now showing 'test' as the current folder. There are three important path markers: dot '.' for the current directory, dot dot '..' for the parent directory, and tild '~' for the home directory.

Going back to the parent directory:
```bash
cd ..
```

Finall, the tild lead you to your home directory:
```bash
cd ~
```

Read this [Bash cheat sheet](https://www.educative.io/blog/bash-shell-command-cheat-sheet) for some additional basic commands.

## Task 2.4: Installing a Programming Language

The last tool we need is Python, the programming language for this course.

On Windows, download and install from [here](https://www.python.org/downloads/windows/). Navigate to 'Latest Python 3 Release' and scroll down to file a Windows installer.

On Mac OS, download and install from [here](https://www.python.org/downloads/mac-osx/). Navigate to 'Latest Python 3 Release' and scroll down to file a Windows installer.

Restart VS Code. open your course folder and open a Terminal. Check your Python installation with:

```bash
python --version
```

This command should return a version number of Python 3.x.x.

TODO install and describe the purpose of pipenv

**What did we achieved?**

* we have a machine ready for developing, executing and sharing Python code.

# Step 3: A Light Bulb

Throughout this course we will control connected light bulb to prototype a service similar to the GoodNight Lamp. Let's have a look to the light bulb in the prototyping kit: the TP-Link LS110 or LS130.

## Task 3.1 Screwing the light bulb

The 101 step of any light bulb is to screw it on a socket, the LS100 series fit on an E27 socket. Make sure it is powered, so that its WiFi is turned on.

## Task 3.2 Installing a Python library

To interact with the light bulb, we will rely on a Python library. A software library is a set of data, piece of code and documentation. In our case, the [python-kasa](https://python-kasa.readthedocs.io/en/latest/index.html) library will help us interact with the light bulb.

Back to VS Code in your course directory, open a Terminal.

We use pip to install Python library. Thanks to the [pipenv setup](#task-2.4), we can install this library inside the course folder only, avoiding any disruption of other Python program on your machine. In the following command,the --pre option signal that we want to install the most recent version of the library, including pre-release.

```bash
pip install python-kasa --pre
```

## Task 3.3 Connecting to the Network

To connect the light bulb to the network, we need to provision it with the WiFi network information. Taken out of [the documentation](https://python-kasa.readthedocs.io/en/latest/cli.html#provisioning), here are the steps:

1. You need to turn on and of the light bulb 3 times in a row. The light bulb blinks a couple of times. This is the way to let it disconnect from any network and start emitting its own WiFi network;
2. Connect your computer to the light bulb network (it should appear as TP-LINK_Smart Bulb_...). Make sure that your machine is not connected to a wired network at the same time.
3. Run the kasa discover command to locate the IP address of the device (likely 192.168.0.1)

```bash
kasa discover
```

TODO screenshot result

When the light bulb is found, at the top of the result you will note 'Host:' followed by 4 digits seperated by dots. This is the IP address of the light bulb on the network, i.e. the address to send messages to it.

* You can scan for the WiFi networks, in case you do not know which one to connect the light bulb to.

```bash
kasa wifi scan
```

TODO screenshot result

* Finally, we send a message to the light bulb with the WiFi network information. In the following command, the host is the IP address of the light bulb identified in step 3, 'wifi join' are the command and subcommand, 'ioSense-net' is the SSID of the network to connect to (i.e. name of the network), the password option provision the network password and keytype is the category of network.

```bash
kasa --host "192.168.0.1" wifi join "ioSense-net" --password iot2017! --keytype="3"
```

If the process works, the light bulbs blinks a couple of time, then connect to the provisioned network. Connect your machine to the same network and run the discover command. Make sure that your machine is not connected to a wired network at the same time, otherwise the discover function might look on the wrong network and find no device.

```bash
kasa discover
```

TODO screenshot result

## Task 3.4 Interacting with the Light Bulb

It is now the time to explore what are the capabilities, using the [documentation](https://python-kasa.readthedocs.io) or the --help option  

```bash
kasa --help
```

TODO screenshot result

TODO a few command examples

# Step 4: A Home Hub

What is a Raspberry Pi, in contrast with an Arduino-like device? Here is a comparison, opposing a ['Microprocessor' and a 'microcontroller'](https://www.youtube.com/watch?v=7vhvnaWUZjE)

Little tour of the Raspberry Pi

Why do we use another computer rather than our laptop? Throughout the course, you will also test your code on your machine. However, when prototyping connected products, you want them to be connected over time, especially for a homehub, and not depending on your laptop activity (e.g. closing the lead, moving out of the house). The Raspberry Pi can be permanently connected and serve its purpose. Besides, it also makes a device on which we can set up network access, enabling your laptop, your phone and other devices to interact with it.

## Task 4.1: Installing the Image

By now your Raspberry Pi image should be ready. Let's go back to Bucket and download it.

TODO intall image on sd card and power the Raspberry Pi with Etcher

TODO look up the IP address of the Raspberry Pi on Bucket

## Task 4.2: Connecting to the Raspberry Pi

You can connect your Raspberry Pi to a screen, a keyboard and a mouse to use it as you would use your own computer. However, while prototyping your Raspberry Pi is often embbedded in your setting and knowing how to handle it remotly is an important skill to have.

Throughout this course, we will thus access the Raspberry Pi remotly. For this we will use the ssh command as follows (replace user and hostname by the one you filled in on Bucket). Pressing enter, you will be prompt for your password.

```bash
ssh username@hostname
```

```bash
ssh userid@hostname
```


## Task 4.3: Controlling the Light Bulb

TODO interact with the lightbulb from the Pi:pipenv, install kasa-python,example commands