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

IAM FEDERATION-------------------------------------------------------------------------------------

Big enterprises usually integrate their own repositories of users with IAM, this way the users can login using to aws console using their
company credentials.

IAM Federation uses SAML standards(Active Directory)

---
