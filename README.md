# F5-Onboarding-Cloudify
 
## Summary:

This method of deploying BIG-IP’s into a Cloudify/Openstack environment will take advantage of as much F5 supported Automation Toolchain components as possible.  While this exercise focuses on creating a cloudify blueprint to deploy BIG-IP, the F5 Automation Toolchain features can be used with other automation tools as well.

For this project, I aimed to create a Cloudify Blueprint which deploys BIG-IP LTM into Openstack. I am using
1) Red Hat Openstack Platform 
2) Cloudify 5.0.5
3) Cloudify-openstack-plugin 2.14.21
4) cloudify-utilities-plugin 1.14

I know there are newer versions of all of these, however, this is what I had at my disposal. I will possibly work on updating some of these in the near future.

The two main features that will be used for Device Onboarding are:
1)	[F5 Cloud-Init](https://clouddocs.f5.com/cloud/public/v1/shared/cloudinit.html), utilizing the tmos_declared module
2)	[F5 Automation Toolchain’s](https://clouddocs.f5.com/) module called [Declarative Onboarding](https://clouddocs.f5.com/products/extensions/f5-declarative-onboarding/latest/)

You have the option of also using the [Application Services 3 (AS3)](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/) module to configure virtual servers in addition to streaming Telemetry to a number of endpoints using F5’s Telemetry Streaming module. 

These can all be downloaded from the F5 Github page: https://www.github.com/f5networks

Summary of Steps
1)	Build custom BIG-IP Qcow2 image using the [F5 Image Generator](https://github.com/f5devcentral/f5-bigip-image-generator/) to modify the qcow2 file you’d like to use by injecting the Automation toolchain RPM's into it.  If you need help with this step, see my notes here: https://github.com/thomsonjames/F5-image-generator-help 
2) Upload that unzipped qcow2 to Openstack


Detailed steps
1)	Build custom BIG-IP Qcow2 image

There are a number of architectural components to onboarding a BIG-IP that would be helpful to have living on the qcow2 image during boot which will make automation much simplere
a)	AS3 service declaratio
