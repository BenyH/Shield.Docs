***********************
Post Installation Steps
***********************


Proxy Configuration
===================

After installing Ericom Shield, the system is ready to use. In order to start browsing securely using Ericom Shield, the Browsing Traffic should be send to an HTTP proxy.

If a Proxy server is already in use (for caching or content filtering purpose), this proxy should be configured to work with Ericom Shield.

Alternatively, the browser will be configured to use the Ericom Shield build-in Proxy.

Integrate with existing proxy

In this cases where the organization already has a proxy server. The existing Proxy server should be configured to connect to the Ericom Shield ICAP server. The ICAP Server is running on the Ericom Shield Server and is listening on port 1433. Configure the exiting server to connect to the Ericom Shield ICAP server on port 1443 using the IP address noted above.

There may also be a need to import the certificates detailed below into the existing proxy server to allow support for https navigation.


Using the EricomShield Service
==============================

The ericomshield service provides the ability to easily perform certain actions on the Ericom Shield system, using a terminal window directly on the host or connected via SSH.

The following actions are available using the service:

* **start**: starts the service
* **stop**: stops the service
* **status**: shows the status of the service
* **version**: shows the service version
* **restart**: stops and restarts the service

The required syntax is sudo service ericomshield <command> e.g.::

	$ sudo service ericomshield status

You should see the following to show that the system is running.

.. figure:: images/ericomshieldstatus_f2.png	
	:scale: 75%
	:alt: Ericom Shield status
	:align: center

	*figure 2: Ericom Shield Status*


End User Configuration
======================

Select your browser of choice and define the Proxy Settings to use the Shield Client IP address (as noted from section 2.2) and 3128 port. These settings can be changed manually as described in the links below, or via Group Policy.

Firefox: 
http://www.wikihow.com/Enter-Proxy-Settings-in-Firefox

Chrome and IE: (*done via the Local Internet Properties*):
https://customers.trustedproxies.com/knowledgebase.php?action=displayarticle&id=10	
	

Configuring Certificates
========================

In order for Shield to handle HTTPS URLs, the following certificate needs to be imported into the client machine (Local Computer). This can be done via Group Policy or manually using the following steps:

Once you have configured your browser to use the Ericom Proxy, opne the browser and go to:

http://install-certificate/ - and download the certificate.

 
**Deploy certificates using Group Policy:**

To deploy certificates using Group Policy, follow the instructions detailed below: 
 
1. Open Group Policy Management Console. 
2. Find an existing or create a new GPO to contain the certificate settings. Ensure that the GPO is associated with the domain, site, or organizational unit whose users you want affected by the policy. 
3. Right-click the GPO, and then select **Edit**. 
4. Group Policy Management Editor opens, and displays the current contents of the policy object. 
5. In the navigation pane, open **Computer Configuration | Windows Settings | Security Settings | Public Key Policies | Trusted Publishers**. 
6. Click the **Action** menu, and then click **Import**. 
7. Follow the instructions in the **Certificate Import Wizard** to find and import the certificate. 
8. If the certificate is self-signed, and cannot be traced back to a certificate that is in the **Trusted Root Certification Authorities** certificate store, then you must also copy the certificate to that store. In the navigation pane, click **Trusted Root Certification Authorities**, and then repeat steps 5 and 6 to install a copy of the certificate to that store. 

	
	
.. note:: More details can be found in this `TechNet Article <https://technet.microsoft.com/en-us/library/cc770315%28v=ws.10%29.aspx?f=255&MSPPError=-2147217396>`_ 


**Manually Installing the Certificate**

.. toctree::
	:maxdepth: 1
	:glob:
	
	../browsers/*


