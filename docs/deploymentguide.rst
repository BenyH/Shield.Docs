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


  .. note:: A higher spec machine will host more virtual containers and therefore more browser sessions.  For example 50 cores and 140GB would support approx. 350 virtual containers.



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
==========

Open a terminal window or connect to the Linux machine using SSH, create a new temporary folder and go to this folder.

Run the following commands.::

	$ wget https://raw.githubusercontent.com/ErezPasternak/Shield/master/Dev-Feb16/ericomshield-setup.sh

	$ sudo chmod +x ericomshield-setup.sh

	$ sudo ./ericomshield-setup.sh

The script may take some time to complete (approx. xx mins). At the end of the script you should see that the deployment is successful.

Ericom Shield is installed in “/usr/local/ericomshield”.


***********************
Post Installation Steps
***********************


Proxy Configuration
===================

After installing Ericom Shield, the system is ready to use. In order to start browsing securely using Ericom Shield, the Browsing Traffic should be send to an HTTP proxy.

If a Proxy server is already in use (for caching or content filtering purpose), this proxy should be configured to work with Ericom Shield.

Alternatively, the browser will be configured to use the Ericom Shield build-in Proxy.

Integrate with existing proxy

In this cases where the organization already has a proxy server. The existing Proxy server should be configured to connect to the Ericom Shield ICAP server. The ICAP Server is running on the Ericom Shield Server and is listening on port 1433. Configure the exiting server to connect to the Ericom Shield ICAP server on port 1443 using the IP address noted in section 2.2

There may also be a need to import the certificates detailed below into the existing proxy server to allow support for https navigation.


Shield Proxy
============

Select your browser of choice and define the Proxy Settings to use the Shield Client IP address (as noted from section 2.2) and 3128 port. These settings can be changed manually as described in the links below, or via Group Policy.

Firefox: 
http://www.wikihow.com/Enter-Proxy-Settings-in-Firefox

Chrome and IE: 
done via the Local Internet Properties: https://customers.trustedproxies.com/knowledgebase.php?action=displayarticle&id=10


Using the EricomShield Service
==============================

The ericomshield service provides the ability to easily perform certain actions on the Ericom Shield system, using a terminal window directly on the host or connected via SSH.

The following actions are available using the service:

* start: starts the service
* stop: stops the service
* status: shows the status of the service
* version: shows the service version
* restart: stops and restarts the service

The required syntax is sudo service ericomshield <command> e.g.::

	$ sudo service ericomshield status

You should see the following to show that the system is running.

.. figure:: images/ericomshieldstatus_f2.png	
	:scale: 75%
	:alt: Ericom Shield status
	:align: center

	*figure 1: Ericom Shield Status*


Browsing HTTPS sites 
====================


**Windows** 

In order for Shield to handle HTTPS URLs, the following certificates need to be imported into the client machine (Local Computer). This can be done via Group Policy or manually. 
 
Download the certificates: 
Save the following certificates locally: 

ca.cert.pem  
https://raw.githubusercontent.com/ErezPasternak/Shield/master/Certs/ca.cert.pem

intermediate-chain.cert.pem		
https://raw.githubusercontent.com/ErezPasternak/Shield/master/Certs/intermediate-chain.cert.pem

 
 
**Deploy certificates using Group Policy:**

To deploy certificates using Group Policy, follow the instructions detailed below: 
 
1. Open Group Policy Management Console. 
2. Find an existing or create a new GPO to contain the certificate settings. Ensure that the GPO is associated with the domain, site, or organizational unit whose users you want affected by the policy. 
3. Right-click the GPO, and then select *Edit*. 
4. Group Policy Management Editor opens, and displays the current contents of the policy object. 
5. In the navigation pane, open *Computer Configuration\|Windows Settings\|Security Settings\|Public Key Policies\|Trusted Publishers*. 
6. Click the *Action* menu, and then click *Import*. 
7. Follow the instructions in the *Certificate Import Wizard* to find and import the certificate. 
8. If the certificate is self-signed, and cannot be traced back to a certificate that is in the *Trusted Root Certification Authorities* certificate store, then you must also copy the certificate to that store. In the navigation pane, click Trusted Root Certification Authorities, and then repeat steps 5 and 6 to install a copy of the certificate to that store. 

	
	
	.. note:: More details can be found in the TechNet Article here…  https://technet.microsoft.com/en-us/library/cc770315%28v=ws.10%29.aspx?f=255&MSPPError=-2147217396


**Manual Installation**
Go to ''Manage Computer Certificates'', and select ''Trusted Root Certification Authorities''

.. figure:: images/Certificateslocalcomputer.png
	:scale: 75%
	:alt: Certificate Store
	:align: center

	*figure 1: Certificate (local computer)*

Right click on “Certificates” in Trusted Root… and select **All Tasks | Import**

.. figure:: images/Certificateslocalcomputer.png
	:scale: 75%
	:alt: Import Certificates
	:align: center

	*figure 1: Import Certificates*


The **Certificate Import Wizard** opens, click **Next** and browse to the folder containing the saved certificates. Select one of them and click **next**, **next** and **Finish** (accepting the defaults). Repeat the process with the second certificate. 

Some browsers, e.g. Firefox, require importing the certificates into the browser itself.

To import the certificates into Firefox, follow these steps: 
Run Firefox, go to **Tools | Options | Advanced | Certificates | View Certificates**. Under the Authorities tab, click **Import**... add the certificate as a trusted authority.  Repeat for the second certificate as well.


**Mac OSX Configuration:**

For instructions on how to import certificates in Mac OS, please visit here...
https://www.sslsupportdesk.com/ssl-installation-instructions-for-apple-mac-os-x-10-11/   

You may have different screens if your Mac is running a different OSX version than the one shown, in such case check with your documentation on the correct method for installing certificates.

