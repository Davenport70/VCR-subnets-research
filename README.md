# TASK 2

## **What is a VPC?**
- Amazon Virtual Private Cloud (Amazon VPC)
- Amazon VPC is the networking layer for Amazon EC2.
- Amazon Virtual Private Cloud (Amazon VPC) lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define
- In order to lock your instances down and secure them against attacks from the outside, you lock them within a VPC. The VPC restricts what sort of traffic, IP addresses and also the users that can access your instances.
## **What are subnets?**
- A subnet is a range of IP addresses in your VPC.
- Subnets are defined as all devices whose IP addresses have the same prefix. For example, all devices with IP addresses that start with 100.100.100. would be part of the same subnet. This would be class C.
- Dividing a network into subnets is useful for both security and performance reasons. IP networks are divided using a subnet mask.

## **What are private and public subnets?**
- public subnets have direct access to the Internet
- private instances do not have direct access

There are essentially 2 components required to make any one of your subnets classed as a public subnet.
- Create and attach an Internet gateway to your VPC.
- add a default route to the route table associated with your subnet. The route could have a destination value of 0.0. 0. 0/0, and the target value will be set as your Internet gateway ID.

## **NACls VS Security Groups? Stateful VS Stateless. (Inbound and outbound)**

***Security groups are stateful:*** This means any changes applied to an incoming rule will be automatically applied to the outgoing rule. e.g. If you allow an incoming port 80, the outgoing port 80 will be automatically opened.

***Network ACLs are stateless:*** This means any changes applied to an incoming rule will not be applied to the outgoing rule. e.g. If you allow an incoming port 80, you would also need to apply the rule for outgoing traffic.

## What is NAC

- NAC (Network Access Control)
- (NAC) has the ability to restrict network access to devices and users that are authorized and authenticated.
- Nac is largely about managing traffic.

**What is NAC used for?**

- Authorization, Authentication and Accounting (AAA) of network connections
- Role-based control for a user, device, or application post-authentication. This means that a given user and their device are placed into their corresponding permission buckets such that an employee in finance and an employee in HR have access to different resources in their environment.
- Confidentiality and containment of intellectual property through policy enforcement.
- Identity and asset management.
- Automatically assess a device’s security posture, and allow or block based on if they pass the security check (which can be based on numerous things, such as operating system version, latest patches installed, a certain anti-virus is installed, etc.)

## **NAC rules for an our Node Sample APP - Public Subnet (Where do clients come in? port 80... You want to login to install stuff? port 22.. you need to communicate to db? )**

-The instances in the public subnet can send outbound traffic directly to the Internet.
- A public subnet means traffic can enter through specific ports, this can give direct access to the app.
- port 22 however is a more secure port and cannot be accessed directly by a user, however the server can access what is inside the database.

## **NAC rules for an our Node Sample APP DB - Private Subnet (Where does traffic come from? and where does it need to go?)**
- The database servers can send and receive Internet traffic through the NAT device in the public subnet, it cannot receive traffic itself directly through its elastic IP address.
-The instances in the private subnet can access the Internet by using a network address translation (NAT) gateway that resides in the public subnet. The database servers can connect to the Internet for software updates using the NAT gateway, but the Internet cannot establish connections to the database servers.
- All traffic is routed through a single IP address.
