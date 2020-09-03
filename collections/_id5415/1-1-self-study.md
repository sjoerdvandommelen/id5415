---
layout: course-page
title: "IoT and Prototyping"
permalink: /module1/self-study
description: "Prototyping Connected Product - Self-Study 1"
self-study-id: 1
self-study-of: id5415-1
tags:
- prototyping
- IoT
- IoT stack
- connected product
- thing
introduction: In this module, the self-study material focus on Prototyping and the Internet of Things' technology stack. We explore the purpose of a functional prototype, in close connection to feasibility testing. Then, we look at connected products, their main characteristics and why they often require a (partially) functional prototype. Finally, we introduce the concept of the Internet of Things (IoT), the technology backbone of connected products.
---

---

* Do not remove this line (it will not be displayed)
{:toc}

---

TODO full self-study

# Prototyping Connected Products

<span class="mdi mdi-text-box-outline"></span> Reading (30 minutes)

In this course, we refer to connected products as any physical entities with the ability to send or receive information through the Internet, in a direct way. It is a touchpoint between the physical and the digital world. Let's define the 2 pillars of connected products: `Things` and `Networks`

The term `Thing` is commonly used to encapsulate the technology enabling physical entities to have a digital manifestation. Clair Rowland distinguishes 4 types of Things:

* **Multipurpose computers** are computers with powerfull [microprocessor](/tags/#microprocessor) such as PCs, laptops, smartphones. These devices are complex digital entities on there own and often not considered as Things. However, in this course, you will sometimes use your laptop as a Thing, when testing the code for an embedded device. 
* **Specialised embedded devices** function on their own for a specific set of functionalities. They have processing capabilities to handle several tasks. Typical examples are smart thermostats or smart watches. They can connect to the Internet on their own or require a connection with a multipurpose computer (e.g. smartphone / smart watch interaction). In this course, the Raspberry Pi represents such a Specialised embedded device. It is a small multipurpose computer which makes it a good candidate for rapid prototyping of connected products.
* **Connected sensors** focus on a specific sensing (or actuation) function and deal with limited resources (e.g. energy, processing, memory). In this course, the light bulb is best representing this type of Things. Prototyping such device requires a focus on hardware, often achieve with arduino-like platform.
* **Passively trackable object** are pieces of metal (e.g. RFID tags) or visuals (e.g. QR code for 'Quick Response' code) which are attached to hardware, connecting them with their digital representation. They require an external device to establish this connection. A typical example is delivery parcels with QR Codes. Throughout the delivery process, parcels are scanned so that customer can trace their location online (digital representation).

The common point of all these Things is their purpose of digitising and communicating information. Thus, the `network`, establishing the communication between these Things, is the second pillar of a connected products. How this communication is established, what constraints does it imply? How fast, reliable, secure is this communication? As the communication is at the core of a connected product, it becomes critical to take it into consideration throughout the design process.

## Opportunities

interactions
data
intelligence


## Challenges
complexity
dynamic
inter-dependence



What is different about prototypes of connected products?

* hardware / software mix
* relying on digital technologies
* distributed, code running in many places
* network
* the senses and 


* Feasibility prototypes
* User Prototypes
* Live-Data Prototypes
* Hybrid Prototypes

* Testing techniques

* What do we mean by prototype
* What for?



## References

1. [Designing Connected Products](https://www.oreilly.com/library/view/designing-connected-products/9781449372682/) UX for the Consumer Internet of Things. By Clair Rowland, Elizabeth Goodman, Martin Charlier, Ann Light and Alfred Lui.

# Internet of Things' Technology Stack

<span class="mdi mdi-video"></span> Video series (30 minutes)

We unpacked the particular prototyping needs for the design and development of connected products. These needs come from the Internet of Things, or the IoT, which is the technology behind product-service systems. Like an iceberg, the physical ‘Things’ are the tip, visible above water while most of the technology and complexity is hidden, immersed underwater.

In the following series of seven small videos, we shed light on this digital technology, mapping its literacy through a layered framework so-called 'stack'. We explore what is the Internet of Things, extracting the key roles of designers in the development of product-service systems.

[Video Series on the Internet of Things' Technology Stack](https://www.youtube.com/playlist?list=PL3sV9hKiYEP-MVdxCXYfl7vei77xdbJo6)


# Check your Understanding

<span class="mdi mdi-head-question"></span> Quiz (15 minutes)

Check your understanding with the following quiz! It is anonymous and you can try as many times as you want!

<iframe width="640px" height= "600px" src= "https://forms.office.com/Pages/ResponsePage.aspx?id=TVJuCSlpMECM04q0LeCIe-EN8Fz6eUZIqbayPT_HeNhUNUFFMUxIMkxGN1Q5NFhSTDBSUTY4V0pNVS4u&embed=true" frameborder= "0" marginwidth= "0" marginheight= "0" style= "border: none; max-width:100%; max-height:100vh" allowfullscreen webkitallowfullscreen mozallowfullscreen msallowfullscreen> </iframe>