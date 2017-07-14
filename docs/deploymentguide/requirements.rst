************
Requirements
************


Software Requirements
=====================

Ericom Shield requires Linux Ubuntu 16.04 and above.

Hardware Requirements
=====================

Minimum hardware specifications are 64GB memory, 8 core processors and 40GB disk space per shield server.



.. note:: A higher spec machine will host more virtual containers and therefore more browser sessions.  For example 50 cores and 140GB would support approx. 350 virtual containers.



Evaluation
==========

The evaluation installation method uses an OVF Virtual Appliance image to allow for speedy deployment. This is described fully in the `Ericom Shield Evaluation Guide <../evaluationguide.html>`_.

Production
==========

For an Ericom Shield production system, you can install using either a Vagrant file or Installation script. It’s recommended to use the Installation script (detailed below).

All deployment options install a dedicated service that first installs Ericom Shield on the machine from scratch. Once done, the service can be used to stop and restart the containers. In addition, Ericom Shield includes an Auto-Update feature to ensure it is always up to date with the latest release. The auto update feature checks for updates each time it is started. 