################
Evaluation Guide
################

>>> IN WORK <<<

**********************
What is Ericom Shield®?
**********************


Ericom Shield is a remote virtual browser solution. The actual browsing takes place in a secure, isolated container that has no access to the Local Area Network.  The Ericom Shield deployment can be on premise in the DMZ or in the Cloud.  Ericom Shield is managed via a web-based administration console.

Ericom Shield enables users to safely browse the internet while protecting the local machine and the network from any malicious code which may execute within the browser. In an event that malicious code is present in the page, it is contained and isolated within the container itself, therefore preventing infection of the local machine or network.  When the session ends, the container is destroyed, and therefore any infection within the container is also destroyed.  

In addition, the Administrator has finite control over file downloads, the system contains black and white lists for any downloads, including a system wide ban of file downloads.  If downloads are allowed, then file sanitization occurs seamlessly in the background before the file is delivered to the user.

Ericom Shield can be used with any browsers and end point device. All that is required is to configure the device (browser) with the location of the Ericom proxy server.

Ericom Shield is deployed on Linux-based containers. Each browsing session starts in its own dedicated container. All sessions are routed by the Ericom Shield Proxy server, ensuring optimal resource allocation and high availability. 


**************************
Ericom Shield Architecture
**************************

.. figure:: images/Architecture_f1.png	
	:scale: 75%
	:alt: Ericom Shield Architecture 
	:align: center

	*Figure 1: Ericom Shield Architecture*
	
A user navigates to a desired web page by entering a URL address in the browser address bar.

HTTP requests are sent to the proxy server (either enterprise or the embedded Shield proxy). The proxy server acts an intermediate and delivers the desired web page to the user.
The proxy server is connected to the Ericom ICAP (Internet Content Adaptation Protocol) server in the Shield Core, which processes the given URL according to the predefined policies (white list, black list etc.) as configured by the Administrator. 

If the URL is not a black listed site then the Shield Core allocates a Shield Browser from the available browser pool, a new dedicated container is assigned for the session and the desired URL is opened and delivered to the user. 
The Shield Browser allows the user a seamless browsing experience, including all commonly used features such as video, audio, printing, downloading, according to the defined policies created by the System Administrator.  

When downloading a file, the downloaded file is first sent to the Content Disarm and Reconstruct (CDR) engine, which is designed to deconstruct the file and remove any content that can cause potential harm (both known and unknown threats). Once the file sanitization is complete, the sanitized file is sent to the user.
	
************
Requirements
************


Ericom Shield is supplied as a Virtual Appliance in Open Virtualization Format (OVF). The minimum requirements for the appliance are: 3GB RAM, 3 processors and 40GB of disk space.

The appliance can be run on any virtualization platform that supports deployment via OVF. The documentation below will provide details of deployment using Oracle Virtual Box. Oracle Virtual Box can be downloaded from `here <http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html>`_

For evaluation purposes, the appliance is limited to a maximum of 20 browser sessions, i.e. 1 user having 20 tabs open or 20 users with a single tab each.

************	
Installation
************

Download the Ericom Shield appliance from `Google Drive <https://drive.google.com/open?id=0B_wcQRaAT_INcXhsc1E4bXlySWs>`_

Importing the Appliance:
========================

*	Open Oracle VirtualBox
*	From the menu, choose ``File Import | Appliance…``
*	select the downloaded file ``shield_eval.ova``
*	When the image has been imported, select the image and click on settings
*	Change the Network setting to ``Bridged Adapter``

.. figure:: images/networksettings.png	
	:scale: 75%
	:alt: Network Settings 
	:align: center

	*Figure 2: Network Settings*
	
	
*	Click ``OK`` to save your settings
*	Start the machine
*	Login using the credentials: ``vagrant/vagrant``
*	You will see the IP Address of your VM, as shown below:  (take a note of this IP address as you will use it later)
	
.. figure:: images/shieldstartupscreen.png
	:scale: 75%
	:alt: Shield Startup Screen 
	:align: center

	*Figure 3: Shield startup screen*	
	
*	Type the following to restart the Ericom Shield Service.  During the restart, Ericom Shield will automatically update itself to the latest version if one is available.::

	$ sudo service ericomshield restart

	Wait until the system is restarted. Once finished, Ericom Shield is ready to handle connections.

*	The ericomshield service is located in ``/usr/local/ericomshield``

If you need to recall the IP address of the appliance at a later date, you can also type::  

	$ sudo ifconfig eth0
	
	
***********************	
Post Installation Steps
***********************

Proxy Configuration
===================
After installing Ericom Shield, the system is ready to use. In order to start browsing securely using Ericom Shield, the Browsing Traffic should be sent to the Ericom HTTP proxy.

For information on how to integrate Ericom Shield with an existing proxy server, see the “Ericom Shield Deployment Guide”.

Shield Proxy
------------
Select your browser of choice and define the Proxy Settings to use the Shield Client IP address (the VM IP address, see “Installation” section) and 3128 port. These settings can be changed manually as described in the links below, or via Group Policy.

**Instructions for common browsers)**
Firefox: http://www.wikihow.com/Enter-Proxy-Settings-in-Firefox
Chrome and IE (done via the Local internet Properties): https://customers.trustedproxies.com/knowledgebase.php?action=displayarticle&id=10


Using the EricomShield Service
==============================

The *ericomshield* service provides the ability to easily perform certain actions on the Ericom Shield system, using a terminal window directly on the host or connected via SSH.

The following actions are available using the service:

*	**start**: starts the service
*	**stop**: stops the service
*	**status**: shows the status of the service
*	**version**: shows the service version
*	**restart**: restarts the service

The required syntax is sudo service ericomshield <command> for example::

	$ sudo service ericomshield status

.. figure:: images/shieldstatus.png
	:scale: 75%
	:alt: Shield Status
	:align: center
	*Figure 3: Shield Status*	
	
.. toctree::
	:maxdepth: 1
	:glob:
	
	https/*


 


	
	
	
	
