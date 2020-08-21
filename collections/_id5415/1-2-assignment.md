---
layout: course-page
title: "Assignment 1"
permalink: /module1/assignment
description: "Prototyping Connected Product - Assignment 1"
assignment-id: 1
assignment-of: id5415-1
introduction: In this assignment, you will set up a Raspberry Pi as a connected home hub to control connected light bulbs. We will walk you through the different steps while exploring the purpose of each component, incrementally drawing an product architecture.
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

We will see in module 5 the concepts of cloud and web services. For now, we will assume that we need something on the Internet that help us collect and visualise data.

Today there are plenty of such cloud services as it is a core component of the IoT technology stack.

In this course we will rely on a set of tools that we developed at IDE to keep control of the functionalities and the data.

Here is a little tour:

TODO Video tour Bucket

Throughout the course, we will rely on these tools to collect and visualise data, but alsoto check the status of our 'Things' on the Internet.

## Task 1.1 Create a DCD Lab account

* connect to Bucket: https://dwd.tudelft.nl/bucket

* Sign in, OAuth2? 

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


# Step 2: Terminal and Python

No worry, we will not start coding before the next module! However, we need to introduce and install (if necessary) two tools in order to interact with the connected light bulb of the prototyping kit.

## Task 1: Terminal

If you laptop rely on Windows


Create a repository 

## Task 2: Python


# Step 3: A Light Bulb

Throughout this course we will control connected light bulb to prototype a service similar to the GoodNight Lamp. Let's have a look to the light bulb in the prototyping kit: the TP-Link LS110 or LS130.

## Task 3.1 Screwing the light bulb



## Task 3.2 



In this step you will use a Raspberry Pi to setup a home hub. This hub will run a program to control the connected light bulb.





# Step 2: A hub

What is a Raspberry Pi

Little tour of the Raspberry Pi

Why do we use another computer rather than our laptop?

* Microprocessor vs microcontroller

https://www.youtube.com/watch?v=7vhvnaWUZjE

You can connect your Raspberry Pi to a screen , a keyboard and a mouse to use it as you would use your own computer. However, while prototyping your Raspberry Pi is often embbedded in your setting and knowing how to handle it remotly is an important skill to have.

Throughout this course, we will thus access the Raspberry Pi remotly.






## Task 1.2: Terminal

* Explore the Raspberry Pi, UNIX environment

terminal, ssh, login, basic terminal commands

localhost, ip

running a command, ctrl+c


# Step 1: Light Bulb

In this step you will start interacting with a connected light bulb from TP-Link and explore its functionalities.

* Control of the light
* Alternative architectures (direct/hub/cloud)


## Task 2.2: Controlling the Light Bulb

* Connected-Home Web server running on the Pi 
* Add light bulb and control it from the hub
