Deployment Guide
============

What is Ericom Shield®?
-----------------------

Ericom Shield is a remote virtual browser solution. The actual browsing takes place in a secure, isolated container that has no access to the Local Area Network. The Ericom Shield deployment can be on premise in the DMZ or in the Cloud. Ericom Shield is managed via a web-based administration console.

Ericom Shield enables users to safely browse the internet while protecting the local machine and the network from any malicious code which may execute within the browser. In an event that malicious code is present in the page, it is contained and isolated within the container itself, therefore preventing infection of the local machine or network. When the session ends, the container is destroyed, and therefore any infection within the container is also destroyed.

In addition, the Administrator has finite control over file downloads, the system contains black and white lists for any downloads, including a system wide ban of file downloads. If downloads are allowed, then file sanitization occurs seamlessly in the background before the file is delivered to the user.

Ericom Shield can be used with any browsers and end point device. All that is required is to configure the device (browser) with the location of the Ericom proxy server.

Ericom Shield is deployed on Linux-based containers. Each browsing session starts in its own dedicated container. All sessions are routed by the Ericom Shield Proxy server, ensuring optimal resource allocation and high availability.

Shield Architecture
^^^^^^^^^^^^^^^^^^^
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

.. topic:: Topic Title

    Subsequent indented lines comprise
    the body of the topic, and are
    interpreted as body elements.
	

.. sidebar:: Sidebar Title
   :subtitle: Optional Sidebar Subtitle

   Subsequent indented lines comprise
   the body of the sidebar, and are
   interpreted as body elements.


.. code:: python

  def my_function():
      "just a test"
      print 8/2
	  
	  
	  
   
Ericom Shield Update...
-----------------------

blah blah....
