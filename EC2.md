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
