******************
Pool Configuration
******************

System Capacity
===============

This is the total number of Browsers that the system will run.  

Available Remote Browser Pool
=============================

This is the minumum number of available browsers.  When the server is started, it will automatically create this number of browsers, so that they are available for users.   As browsers are taken, the system will automatically create new ones to maintain this minimum value.

In order to increase security and resource utilization, shield will disconnect idle sessions, while when the system is not loaded, the idle timeout is 10 hours, when the system is loaded this timeout is set to lower value.


System Load Index Max Threshold
===============================

This is the system capacity threshhold in % terms.  Once this value is reached, the system will use the Load Idle Timeout setting. 


System Load Index Min Threshold
===============================

This is the lower capacity threshhold, if the system is running lower that the set threshhold, the default idle timeout is used.


Standard Idle Timeout
=====================

Enter the standard timeout value in minutes.
 
 
Load Idle Timeout
=================
Enter the load idle timeout value in minutes.