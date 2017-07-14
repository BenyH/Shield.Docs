**********
Installers
**********

Evaluation
==========

The evaluation installation method uses an OVF Virtual Appliance image to allow for speedy deployment. This is described fully in the `Ericom Shield Evaluation Guide <../evaluationguide.html>`_.

Production
==========

For an Ericom Shield production system, you can install using either a Vagrant file or Installation script. It’s recommended to use the Installation script (detailed below).

All deployment options install a dedicated service that first installs Ericom Shield on the machine from scratch. Once done, the service can be used to stop and restart the containers. In addition, Ericom Shield includes an Auto-Update feature to ensure it is always up to date with the latest release. The auto update feature checks for updates each time it is started. 


Virtual Appliance
=================

Prerequisites
-------------

VirtualBox on Windows/Linux:

Linux: open a terminal and run::
 
	$ apt install virtualbox 

For Windows, download from... https://www.virtualbox.org/wiki/Downloads


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

Create a folder with the name: ``Vagrant``. Change to this folder by typing ``cd Vagrant`` and then run the following commands::

	$ “wget https://raw.githubusercontent.com/ErezPasternak/Shield/master/Dev-Feb16/Vagrantfile”
	$ chmod +x Vagrantfile
	$ vagrant up
	

	

.. note:: The “vagrant up” command may take a while to complete, especially if this is the first time you have run this command on the machine.



After the process is successfully completed, the user is displayed with the following data: the VM’s IP and several ports of interest.


Installation Script
===================

Prerequisites
-------------

Ubuntu 16.04 - to install, follow the instructions `here <https://www.ubuntu.com/download/desktop/install-ubuntu-desktop>`_

Deployment
----------

Open a terminal window or connect to the Linux machine using SSH, create a new temporary folder and go to this folder.

Run the following commands::

	$ wget https://raw.githubusercontent.com/ErezPasternak/Shield/master/Dev-Feb16/ericomshield-setup.sh
	$ sudo chmod +x ericomshield-setup.sh
	$ sudo ./ericomshield-setup.sh

The script may take several minutes to complete. At the end of the script you should see that the deployment is successful.

Ericom Shield is installed in ``/usr/local/ericomshield``.