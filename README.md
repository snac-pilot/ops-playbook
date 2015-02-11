# SNAC Pilot Operations Playbook

This repository is for publicially accessible notes regarding the
operation of the SNAC Pilot website and technical infrastructure,
and related scripts and routines.

(use the wiki too)

## Amazon Web Services

A new Amazon Web Services account shall be set up, and CDL's master
AWS account shall be linked as the payee.  Using that master account,
CDL will set up [IAM](http://aws.amazon.com/iam/) accounts, roles,
and policies such that regular access will not directly access the
master account.

Google authenticator or other [multi
factor](http://aws.amazon.com/iam/details/mfa/) auth token
shall be used to access the AWS console.

Amazon access keys shall only be issued with very limited access
policies.  Most access should be through IAM accounts or roles.

## Multi A-Z

In order to design a fault tolerant application in AWS, it is
recommended to use multiple availability zones.  For example,
`us-east-1b` and `us-east-1e` are two AZs located in two physically
seperate datacenters in Virginia.

[RDS for Postgres](http://aws.amazon.com/rds/postgresql/), for 
example, offers "Multi-AZ Deployments" where a hot spare is
kept in sync in a second AZ.  If a whole datacenter goes down, 
the database will fail over.
