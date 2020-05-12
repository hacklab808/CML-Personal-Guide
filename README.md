# Getting started with Cisco Modelling Labs (Personal and Enterprise)

Cisco Modeling Labs is a tool for building virtual network simulations (or labs) for you to test out new topologies, protocols, and config changes; automate network tests via CI/CD pipeline integration; and learn new things about the cool world of networking. Cisco Modelling Labs 2 has been rebuilt from the ground up, with an all new HTML5 user interface and smaller footprint allowing for much greater performance in simulations.

In the Network simulation is becoming an increasingly important area, particuarly with organisations looking to adopt network automation, we often need safe environments where we can test and understand our automation tooling is working correctly so that when we deploy to production networks we know what we're expecting to happen.

One of the key usecases of CML-2 is for integrating in CICD pipelines. A big advantage of CML-2 over other simulation systems is the new REST API which allows us to automate the creation and running of simulations. After doing an intitial introduction of CML we'll explore the API and understand how it can be leveraged.

## Sandbox environment / Prerequsites 

To follow this lab you will need an instance of CML2. For this you have 2 options the first to build your own environment or to use the prebuilt DevNet sandbox.

If you are looking to build your own CML environment you'll first need to purchase licenses for  limited to 20 nodes Can be purchased for $199. If you are interested in purchasing CML Personal you can do so from this [link](https://learningnetworkstore.cisco.com/cisco-modeling-labs-personal/cisco-cml-personal) 

There is also a Enterprise edition which allows a higher node count and more flexibility, for more information on this reach out to your Cisco account team or a Cisco partner. What you will read on this guide is working with personal however the underlying system between Personal and Enterprise is similar therefore things like the API and functionality we discuss is applicable. 

Alternatively and what I'd recommend doing if you're just starting out and just want to get to grips with CML  is to use the excellent DevNet sandbox where you can reserve an instance of CML2 for up to 4 hours. This sandbox provides access to a Cisco Modeling Labs system that can be used to explore the capabilities of the newest release of Cisco Modeling Labs. This is quite a generous system with almost 40GB of RAM and 57GB of disk space so theres space to do some pretty decent simulations. All DevNet sandboxes are completely free and can be accessed within seconds.

https://developer.cisco.com/docs/sandbox/#!overview/all-networking-sandboxes 

## The Basics

If you're using the sandbox when you first login there's already a premade simulation you can try out. I'm going to stop and delete this for now and walk you through the process of creating you're own simulation but feel free to explore the simulation to get to grips .

Cisco Modeling Labs supports many platforms – Today Cisco Modeling Labs supports the following nodes:
IOSv and IOSvL2
NX-OSv and NX-OS 9000v
IOS XRv and IOS XRv 9000
IOS XE (CSR1000v)
ASAv
Supporting systems including Linux boxes, WAN emulators and Traffic simulations and more 

### Creating a topoloy

First thing we need to do is create a topology, in this we're going to keep it simple and build a topology with 2x CSR1000v devices and connect them together through a WAN emulation box. To do this click on the +Add Lab button on the top right and create a lab, then select you're newly created lab from the simulations pane

When you enter into the lab, you'll be greeted with your canvas. Drag your devices you want onto the canvas, in the case below i've selected 2 CSR1000v devices and a WAN emulation device. To create links over the devices hover your cursor over the node you wish to connect from and select the blue link icon, hold your mouse down and drag it to the device you want to connect to. A small dialogue box should appear and allow you to select the exact port. Cable your devices as we have in the graphic below.

![add-lab](images/add-lab.gif)

To power on the devices hover your cursor over the devices and select the green power on option, give the devices a couple of minutes to allow CML to boot them up. 

![power-on](images/power-on.gif)

You can feel free to make some config to the devices if you'd like by going into the console and configuring the devices. Feel free to explore the simulation options and add some other nodes in too. Otherwise congratulations you've just built your first simulation.

Tip: A really nice simple feature is the WAN emulation node that I've included in our simulation. This acts as a purely layer 2 node can be configured to simulate a variety of transport methods really easily. To configure the WAN emulation go to the console of the device and enter option 1, select profile to see what options you have. Alternatively you can tweak the bandwidth, loss, jitter and latency yourself.

![wan-emulation](images/wan-em.gif)

### Importing a topology

## Automation

### The API

One of the real advantages of this version of CML is the excellent API which allows us to automate many of the common tasks when using CML. As mentioned previously this could allow for integration into a CICD pipeline. 

Tasks we could automate include:

* Spin up and down simulations
* Edit simulations while running (add extra link, add node etc)
* Get detailed information from devices on a simulation
* Conduct actions such as a packet capture

### Python SDK
