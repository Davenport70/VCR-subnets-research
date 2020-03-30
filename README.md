# TASK 2

## **What is a VPC?**
- Amazon Virtual Private Cloud (Amazon VPC)
- Amazon VPC is the networking layer for Amazon EC2.
- Amazon Virtual Private Cloud (Amazon VPC) lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define
## **What are subnets?**
- A subnet is a range of IP addresses in your VPC.

## **What are private and public subnets?**
- public subnets have direct access to the Internet
- private instances do not have direct access

There are essentially 2 components required to make any one of your subnets classed as a public subnet.
- Create and attach an Internet gateway to your VPC.
- add a default route to the route table associated with your subnet. The route could have a destination value of 0.0. 0. 0/0, and the target value will be set as your Internet gateway ID.

## **NACls VS Security Groups? Stateful VS Stateless. (Inbound and outbound)**

***Security groups are stateful:*** This means any changes applied to an incoming rule will be automatically applied to the outgoing rule. e.g. If you allow an incoming port 80, the outgoing port 80 will be automatically opened.

***Network ACLs are stateless:*** This means any changes applied to an incoming rule will not be applied to the outgoing rule. e.g. If you allow an incoming port 80, you would also need to apply the rule for outgoing traffic.

## **NAC rules for an our Node Sample APP - Public Subnet (Where do clients come in? port 80... You want to login to install stuff? port 22.. you need to communicate to db? )**

## **NAC rules for an our Node Sample APP DB - Private Subnet (Where does traffic come from? and where does it need to go?)**
