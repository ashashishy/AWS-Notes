IAM (Identity and Access Management)

Consists of Users, roles and groups

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

You recevice cloudtrail log records that include information about iam identities who made request for aws resources in your account

Use access keys to make programatic requests to aws. Access key and secret access key can only be generated once.

Iam is eventually consistant. Iam achieves high availibility by replicating data across multiple servers with in aws data centers around the globe.

Unique account signin page URL:
https://my_account_id.signin.aws.amazon.com/console/

Use iam tags to add custom tags of key value pairs.

IAM FEDERATION
Big enterprises usually integrate their own repositories of users with IAM, this way the users can login using to aws console using their
company credentials.

IAM Federation uses SAML standards(Active Directory)

Identity federation can be used to get temporary access to aws account

<h2>INFRASTRUCTURE ELEMENTS</h2>
        <h3>Principle</h3>

        An entity that can make a request for an action or operation
