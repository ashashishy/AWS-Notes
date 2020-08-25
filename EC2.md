<h1>EC2</h1>

Renting virtual machines(EC2)
Storing Data on virtual drives(EBS)
Distributing load accross machines(ELB)
Scaling the services using auto scaling group

<b>Launching an Ec2 Instance</b>
choose Ami->choose Instance Type->configure Instance->Add storage->Add tags->Configure security group->review->launch

Connect to Ec2 inctance using

SSH
Putty
Instance connect

                        Port 22

ssh----------------------------------------------------->EC2 Instance

command:
chmod 0400 keyname.pem
ssh -i keyname.pem ec2-user@publicipofinstance

limit is 20 reserved instances per account
Ami or amazon machine images are different operating systems and packages that can be used as templates

instance types include
t-type and m-type for general purpose
c-type for compute optimized
r-type, x-type and z-type for memory optizimized
d-type, h-type and i-type for storage optimized
f-type, g-type and p-type for accelerated computing

secure login using keypair

storage volumes delete temporary data when you stop or terminate instances.
instnaces with instance store volumes can only be terminated
instances with Ebs storage can be stopped and terminated

for persistance data use EBS
Multiple physical loacations such as regions and AZs for deploying resources such as ec2 instances and EBS storages
Security grups are firewalls that determine who can access the instnaces based on ip address hostname and ports

Elastic ip address do not change when instance restarts
limit-5 elastic ips per accound

use tags to identify instances

VPCs are logical isolations that are separate from aws cloud, you can launch instances in vpcs

user-data are scripts that automatically run when an instance launches

Host recovery for ec2 instance autmoatically launches new isntance in a new host in the event of an unexpected hardware failure on a dedicated host.

when an instance is in stopped state you can change the instance type, attach detach ebs, change ram, kernal

previously to launch an encrypted EBS-backed ec2 instance from an unencrypted ami, you would first need to create an encrpyted copy of the ami and use that to launch ec2 instance. Now you can do that directly from unencrypted ami.

You can copy ami to different regions

<h3>Pricing</h3>

On Demand- Pay for what you use with no long-term commitment or upfront payment

Reserved-pay low hourly rate with long term commitment of 1 to 3 years. standard and convertible offerings
Standard offering provide the most significant discount but you can only modify some of its attributes.
Convertible offering provides lower discount than the standard one but you can be exchanged with another convertible reserved instance with different attributes.

Spot Instances- request unused ec2 instances which can significantly lower your cost. They are available at a discount of 90% compared to on demand instances.
Spot instances with defines durations also known as spot blocks are designed not to be interrupted and will run countinously for the duration you selected. this makes them perfect for jobs that take finite time to complete like batch processing, encoding and rendering, modeling and analysis, and countinous integration.
A spot fleet is a collectiion of spot instances and optionally on demand instances. The service attempts to launch number of spot instances and on demand instances to meet your specified capacity.The splot fleet also tries to maintain the target capacity even if the spot intsances are interrupted.
A spot instance pool is a set of unused ec2 instances with same instace types, operating system, availibility zone and network platform.
You can start and stop your spot instances that are backed by amazon EBS.

Dedicated Hosts- pay for the physical host that is fully dedicated to running your instances, and bring your existing per-socket, per-core, or per-vm software liscence to reduce cost.

Dedicated Instance-Pay by the hour for instances that run on a single tenant harware.

There is a data transfer charge for copying ami from one region to another.
Ebs pricing is different from instance pricing
Aws imposed a small hourly charge if an elastic Ip is not associated with a running instance or if it is associate with a stopped instance of unattached network interface.
You are charged for an additional elastic ip address associated with an instance

If data is transferred between two instances it is charged for data transfer out from another regions for the first instance to data transder in from another region for the second region.

<h3>Security</h3>

Use iam to controll access to your intances.||Iam policies||Iam Roles.||
Restrict access by only allowing trusted hosts or networks to access ports on your instance.
A security group acts as a virtual firewall that controlls traffic for one or more instances.
Create different security groups for instances that have different security requirements.
You can add rules to security groups that allow traffic to or from its associated instances.
YOu can modify the rules of security group at any time.
New rules are automatically applied to all the instances that are associated with the security group.
Evaluation of all the rules associated with the security group to decide weather to allow or deny traffic
By default security groups allow all outbound traffic and deny all inbound traffic.
security group rules are permissive, you can't create a rule to deny access.
security groups are stateful.
If you dont specify any security group while launching an instance, it is associated with the default security groups of that vpc and has the following rule.
Allow all inbound traffic from instances associated with the default security group.
Allow all outbound traffic from the instance.
Disable password based logins for instances launched from your ami, since passwords can be cracked or found.

<h3>Networking</h3>
An elastic ip address is a static ipv4 address designed for dynamic cloud computing. with it you can mask the failure of an instnace or application by rapidly remapping that ip with another instance.
If you have not enabled auto assign public ip with your instance, you need to assign an elastic ip to the instance to communicate with the internet
An elastic ip is for use in a specific region only
BY default all aws accounts are limited to have only 5 elastic ip address per region because ipv4 address are scarce.
By default all ec2 instances come with a private ip.
An elastic network is a virtual network interface card that directs traffic to the instnaces.
Every intance in a vpc has a network interface call primary network interface(eth0) which cannot be detached.
You can create additional network interfaces. the maximum interface varries based on the instnace type.
You can attach a network interface to an intance in different subnet as long as it is in same Az.
Default interfaces are terminated with instance termination
Scale with ec2 scaling grup and distribute traffic with elastic load balancer
You can configure your instances as bastion host aka(jump boxes) in order to access your vpc instances for management, using ssh or RDP protocol
A bastion host is a server whose purpose is to provide access to a private network from an external network, such as the Internet. Because of its exposure to potential attack, a bastion host must minimize the chances of penetration.

<h3>Monitoring</h3>
EC2 items to monitor.
CPU utilication, network utilization, disk performance, disk read/writes using ec2 metrics
memory utilization, disk swap utilization, disk space utilization, page file utilization, log collection using monitorind agent/ cloudwatch logs.

system status check- monitor the aws instance require to use your instance to ensure they are working properly. They checks detect problems with your instnace that require aws involvement to fix

instnace status check- monitor software and network configuration of individual instances. this checks detect problems that are to be fixed by you

cloudwatch alarm- watch a single metric over time that you specify and perform action based on the value of the metrics relative to the given metric over a number of time period.

Aws cloudwatch events- automate your aws services and respond automatically to system events.

Aws cloudwatch logs- monitor store and access log files from ec2 instances, cloudtrail and other services

MOnitor ec2 instnaces with aws cloudwatch, by default ec2 sends metric data every 5 minutes

<h3>Placement Groups</h3>
Placement groups determine how instances are placed on an underlying physical harware.

cluster- cluster instances are placed on a same underlying harware for low letency and high network throughput or both in a single availibility. Good for instnaces whos network traffic is between each other.

spread- spread instances are placed on different harwares. Recommended for applications that have small number of critical applications that should be kept seperate from each other.A spread placement group can span multiple availibility zones and you can have maximum of seven instances per availibility zone per placement group.

Partition placement group is an ec2 placement strategy in which the ec2 instances spread accross logical partition and make sure intances from different partition do not share same underlying hardware

<h3>Rules</h3>
The name you specify for the placement group must be unique within your aws account for the region
You cant merge placement groups 
An instance can be launched in one placement group at a time, it cannot span multiple placement groups
Instance be tenancy host cannot be launched in a placement group
