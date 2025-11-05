Network Access Control (NAC)

NAC solutions are systems that ensure only authorized and compliant devices and users can connect to a network. These solutions prevent unauthorized access, and they enforce corporate security policies by checking devices for compliance, such as verifying that antivirus software is active and updated.

How it works

* Authentication: NAC verifies the identity of users and devices, often using methods like multifactor authentication or specific credentials.  
* Policy Enforcement: Administrators define security policies to determine which users and devices are allowed to connect and what level of access they have.  
* Access Control: Based on the authentication and compliance checks, NAC can grant, deny, or quarantine access to the network.  
* Network visibility: provide a comprehensive inventory of all users, devices and their access levels, and help uncover unknown devices on the network.

AAA Framework 

AAA framework refers to the Authentication, Authorization, and Accounting model, which controls access to devices and networks. It works by first authenticating a user's identity, then authorizing what they are allowed to do, and finally accounting for their activity by logging it for auditing and security purposes.

Authentication: Verifies a user's identity to ensure they are who they claim to be, using a username and password

Authorization: Manages what an authenticated user is permitted to do on a network, such as granting different levels of access to different users

Accounting: Tracks and logs users activities, such as the time they spend on the network, the resources they access, and the traffic they generate. This is used for monitoring, auditing, and compliance

Implementation

To implement a Network Access Control solution with a Captive Portal, we’re going to use pfSense’s Captive Portal using FreeRADIUS, combining two core pieces of network authentication and access control: 

1\. Captive Portal \- a web page that intercepts users trying to access the network, where they must authenticate before gaining full access.

2\. FreeRADIUS \- A RADIUS server that will handle authentication, authorization, and accounting

The FreeRADIUS will work as an AAA server and the captive portal will interact with FreeRADIUS for user authentication

Why pfSense?

* VPN integration: it supports remote-access VPNs, allowing to secure remote connections from workers at home while controlling what traffic goes through the VPN tunnel  
* Cost-effectiveness: it’s a free open-source software, so it’s a cost-effective and sustainable solution  
* Flexibility and customization: as an open-source platform, you can tailor it to your specific needs, integrating other open-source tools, such as FreeRADIUS, to enhance its capabilities  
* Scalability: it can be applied to networks of various sizes, so it can keep pace with the company's growth

Why a combining a captive portal with FreeRADIUS

* Centralized authentication: FreeRADIUS centralizes user authentication, so you can manage user access from a single point and integrate with existing databases, in this case we will integrate it with the Active Directory database  
* Enhanced Security: the captive portal ensures that only authenticated users can access the network, preventing unauthorized access and protecting the network from potential threats  
* Detailed accounting: FreeRADIUS can track user activity, providing detailed accounting for monitoring purposes  
* Flexible user management: users can be authenticated against an Active Directory’s database  
* Scalability: the setup is scalable for different environments, such as managing guest Wi-Fi or managing access for many users

Implementing Captive Portal

1. In pfSense, go to Services \> Captive Portal.  
     
     
     
   

2. Create a zone on the LAN interface

