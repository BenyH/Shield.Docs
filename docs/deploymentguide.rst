################
Deployment Guide
################

***********************
What is Ericom Shield®?
***********************

Ericom Shield is a remote virtual browser solution. The actual browsing takes place in a secure, isolated container that has no access to the Local Area Network. The Ericom Shield deployment can be on premise in the DMZ or in the Cloud. Ericom Shield is managed via a web-based administration console.

Ericom Shield enables users to safely browse the internet while protecting the local machine and the network from any malicious code which may execute within the browser. In an event that malicious code is present in the page, it is contained and isolated within the container itself, therefore preventing infection of the local machine or network. When the session ends, the container is destroyed, and therefore any infection within the container is also destroyed.

In addition, the Administrator has finite control over file downloads, the system contains black and white lists for any downloads, including a system wide ban of file downloads. If downloads are allowed, then file sanitization occurs seamlessly in the background before the file is delivered to the user.

Ericom Shield can be used with any browsers and end point device. All that is required is to configure the device (browser) with the location of the Ericom proxy server.

Ericom Shield is deployed on Linux-based containers. Each browsing session starts in its own dedicated container. All sessions are routed by the Ericom Shield Proxy server, ensuring optimal resource allocation and high availability.

*******************
Shield Architecture
*******************
.. figure:: images/Architecture_f1.png	
	:scale: 75%
	:alt: Ericom Shield Architecture 
	:align: center

	*figure 1: Ericom Shield Architecture*



A user navigates to a desired web page by entering a URL address in the browser address bar.

HTTP requests are sent to the proxy server (either enterprise or the embedded Shield proxy). The proxy server acts an intermediate and delivers the desired web page to the user.

The proxy server is connected to the Ericom ICAP (Internet Content Adaptation Protocol) server in the Shield Core, which processes the given URL according to the predefined policies (white list, black list etc.) as configured by the Administrator.

If the URL is not a black listed site then the Shield Core allocates a Shield Browser from the available browser pool, a new dedicated container is assigned for the session and the desired URL is opened and delivered to the user.

The Shield Browser allows the user a seamless browsing experience, including all commonly used features such as video, audio, printing, downloading, according to the defined policies created by the System Administrator.

When downloading a file, the downloaded file is first sent to the Content Disarm and Reconstruct (CDR) engine, which is designed to deconstruct the file and remove any content that can cause potential harm (both known and unknown threats). Once the file sanitization is complete, the sanitized file is sent to the user.

************
Key Features
************

Ericom Shield has the following key features:

* Enables users to browse the internet safely and securely while isolating the users’ machine and the internal network from threats of malware and ransomware.

* Seamless user experience with zero installation on the end point devices – users benefit from the same experience as a non-protected browser, but without the risks.

* Rich web based administration console, supported by all browsers. The Admin interface does not require any high maintenance plug-ins or installers.

* Includes a policy engine to allow Administrators to easily manage which sites users can access, download files, store cookies etc.



******************
Installation
******************


Software Requirements
=====================

Ericom Shield requires Linux Ubuntu 16.04 and above.

Hardware Requirements
=====================

Minimum hardware specifications are 64GB memory, 8 core processors and 40GB disk space per shield server.

Note

A higher spec machine will host more virtual containers and therefore more browser sessions.  For example 50 cores and 140GB would support approx. 350 virtual containers.



Evaluation
==========

The evaluation installation method uses an OVF Virtual Appliance image to allow for speedy deployment. This is described fully in the “Ericom Shield Evaluation Guide”.

Production
==========

For an Ericom Shield production system, you can install using either a Vagrant file or Installation script. It’s recommended to use the Installation script (detailed below).

All deployment options install a dedicated service that first installs Ericom Shield on the machine from scratch. Once done, the service can be used to stop and restart the containers. In addition, Ericom Shield includes an Auto-

Update feature to ensure it is always up to date with the latest release. The auto update feature checks for updates each time it is started. 

**********
Installers
**********

Virtual Appliance
=================

Prerequisites
-------------

VirtualBox on Windows/Linux:

Linux: open a terminal and run:: 

$ apt install virtualbox · Windows: https://www.virtualbox.org/wiki/Downloads

Vagrant File
============

Prerequisites
-------------

The first step is to install Vagrant and VirtualBox on Ubuntu, as detailed above, please ensure that your Ubuntu server is 16.04 or above.

To install, open a terminal window or SSH to the Linux machine and run::

	$ apt install vagrant

	$ apt install virtualbox


Deployment
----------

Create a folder with the name: “Vagrant”. Change to this folder by typing “cd Vagrant” and then run the following commands.::

	$ “wget https://raw.githubusercontent.com/ErezPasternak/Shield/master/Dev-Feb16/Vagrantfile”

	$ chmod +x Vagrantfile

	$ vagrant up

	.. note:: The “vagrant up” command may take a while to complete, especially if this is the first time you have run this command on the machine.

After the process is successfully completed, the user is displayed with the following data: the VM’s IP and several ports of interest.


*******************
Installation Script
*******************

Prerequisites
=============

Ubuntu 16.04 - to install, follow these instructions: https://www.ubuntu.com/download/desktop/install-ubuntu-desktop

Deployment
----------

Open a terminal window or connect to the Linux machine using SSH, create a new temporary folder and go to this folder.

Run the following commands.::

	$ wget https://raw.githubusercontent.com/ErezPasternak/Shield/master/Dev-Feb16/ericomshield-setup.sh

	$ sudo chmod +x ericomshield-setup.sh

	$ sudo ./ericomshield-setup.sh

The script may take some time to complete (approx. xx mins). At the end of the script you should see that the deployment is successful.

Ericom Shield is installed in “/usr/local/ericomshield”.
