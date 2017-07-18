***********************	
Post Installation Steps
***********************

Proxy Configuration
===================
After installing Ericom Shield, the system is ready to use. In order to start browsing securely using Ericom Shield, the Browsing Traffic should be sent to the Ericom HTTP proxy.

For information on how to integrate Ericom Shield with an existing proxy server, see the `Ericom Shield Deployment Guide <../deploymentguide/postinstallationsteps.html>`_.

End User Configuration
======================

Select your browser of choice and define the Proxy Settings to use the Shield Client IP address (the VM IP address, mentioned `here <http://shielddocs.readthedocs.io/en/latest/evaluationguide/installation.html#installation>`_) and 3128 port. These settings can be changed manually as described in the following links, or via Group Policy.

**Instructions for common browsers**

`Firefox <http://www.wikihow.com/Enter-Proxy-Settings-in-Firefox>`_

`Chrome and IE <https://customers.trustedproxies.com/knowledgebase.php?action=displayarticle&id=10>`_ (done via the Local internet Properties)
	

Configuring Certificates
========================

In order for Shield to handle HTTPS URLs, the following certificate needs to be imported into the client machine (Local Computer). This can be done via Group Policy or manually using the following steps:

Once you have configured your browser to use the Ericom Proxy, open the browser and go to `install-certificate <http://install-certificate/>`_ and download the certificate.

**Installing the Certificate**

.. toctree::
	:maxdepth: 1
	:glob:
	
	../browsers/*

	
Using the EricomShield Service
==============================

The EricomShield service provides the ability to easily perform certain actions on the Ericom Shield system, using a terminal window directly on the host or connected via SSH.

The following actions are available using the service:

*	**start**: starts the service
*	**stop**: stops the service
*	**status**: shows the status of the system
*	**version**: shows the system version
*	**restart**: restarts the service

The required syntax is systemctl <command> ericomshield for example::

	$ systemctl status ericomshield

	
.. figure:: images/shieldstatus.png
	:scale: 75%
	:alt: Shield Status
	:align: center
	
	*Figure 3: Shield Status*	

