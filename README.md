# F5-Onboarding-Cloudify
 
Summary:
This method of deploying BIG-IP’s into Cloudify will take advantage of as much F5 supported Automation Toolchain components as possible.  While this exercise focuses on creating a cloudify blueprint to deploy BIG-IP, the F5 Automation Toolchain features can be used with other automation tools as well.

The two main features that will be used for Device Onboarding are:
1)	[F5 Cloud-Init] (https://clouddocs.f5.com/cloud/public/v1/shared/cloudinit.html), utilizing the tmos_declared module
2)	[F5 Automation Toolchain’s] (https://clouddocs.f5.com/)  [Declarative Onboarding] (https://clouddocs.f5.com/products/extensions/f5-declarative-onboarding/latest/)

You have the option of also using the Application Services 3 (AS3) module to configure virtual servers in addition to streaming Telemetry to a number of endpoints using F5’s Telemetry Streaming module. 

Summary of Steps
1)	Build custom BIG-IP Qcow2 image 
a.	qcow2 file you’d like to use
b.	cloud-init module to support static management IP
c.	install rpm files for automation toolchain


Takes Advantage of supported F5 Automation Toolchain features such as Declarative Onboarding (DO), Application Services Template 3 (AS3), and Telemetry Streaming (TS).




Detailed steps
1)	Build custom BIG-IP Qcow2 image

There are a number of architectural components to onboarding a BIG-IP that would be helpful to have living on the qcow2 image during boot which will make automation much simplere
a)	AS3 service declaratio
