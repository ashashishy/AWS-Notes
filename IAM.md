<h3>IAM (Identity and Access Management)</h3>

<p>Consists of Users, roles and groups

Root account should never be shared or used(it has the most power)

Users must be created with proper permission

IAM is the center of AWS

Policies are written in json

Each user should have his own account

Roles are something we give to machine

One IAM role per application

Policies are which define what each user, role and group can do

IAM has a global view

Permissions are governed by Policies

IAM has predefines managed policies

Follow least privilage principles

Never share IAM credentials with anyone

Never write IAM credentials in code

You can use IAM features to securely provide credentials to your applications which provides permissions to your application to access aws resources.

You receive cloudtrail log records that include information about iam identities who made request for aws resources in your account

Use access keys to make programatic requests to aws. Access key and secret access key can only be generated once.

Iam is eventually consistant. Iam achieves high availibility by replicating data across multiple servers with in aws data centers around the globe.

Unique account signin page URL:
https://my_account_id.signin.aws.amazon.com/console/

Use iam tags to add custom tags of key value pairs.

<h3>IAM FEDERATION</h3>
Big enterprises usually integrate their own repositories of users with IAM, this way the users can login using to aws console using theircompany credentials.

IAM Federation uses SAML standards(Active Directory)

Identity federation can be used to get temporary access to aws account</p>

<h2>INFRASTRUCTURE ELEMENTS</h2>
        <h3>Principle</h3> 
An entity that can make a request for an action or operation.
Your account root user is your first principle

<h3>Requests</h3>
When a priciple tries to user the aws console, aws api or cli that principle sends a request to aws

Request includes the following information
• Action or Operation- The action or operation that the principle wants to perform
• Resource- the aws resource on which the action or operation is to perform
• Principle- the user, role, federated user or application that sends the request. Information about the principle  
 includes the policies that are associated with that principle.
• Environment Data- Information about the ip address, user agent, time of the day
• Resource Data- data related to the resource being requested.

<h3>Authentication</h3>
To authenticate from console you must provide your username and password
To authenticate from cli you must provide your access key and secret access key using aws configure

<h3>Authorization</h3>
Aws uses values from request contex to check for policies that apply to the request. It then uses those policies to determine whether to allow or deny that request.

Policies can be categorized as permissions policies or permissions boundaries.
permissions policies define the permissions of the object to which they are attached. This includes identity based policies, resource based policies and ACLs.

Permissions boundaries is an advance feature that uses policies to limit the maximum permissions that a principle can have.

To provide users with permissions to use the aws resouces that they need, we used idenity based policies.

<b>Resource based policies are used for cross account access</b>

Evaluaiton logic for policies:

BY default all requests are denied.
An explicit allow permission in policy overwrites this default

A permission boundary overwrites allow. if there is a permission boundary applied, the permission boundary must allow the request otherwise it is implicitly denied.

An exolicit deny in any policy overwrites any allow.
