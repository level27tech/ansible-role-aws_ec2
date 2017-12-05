level27tech.aws_ec2
==========

This role enables you to create Amazon Web Services (AWS) Elastic Compute Cloud (EC2) Instances.  It performs the following functions:

* Creates the EC2 instance
* Optionally, adds a DNS A record for the private IP address
* Optionally, adds the EC2 instance to the specified Ansible groups

All objects, where possible will include a Name tag and a chosen Project tag.

Requirements
------------------

In order to use this role you need an AWS account and an AWS user with appropriate permissions. 
To make things easier an AWS policy document is included with this role.

>AnsibleEC2Policy.json

As this role interfaces with the AWS API, the boto Python module is also required.
One way to install boto is to use pip:
> pip install boto

Role Variables
-------------------

The role includes the following defaults:

**AWS Credentials**

*Note that these credentials should be kept private as they can be used to gain access to your AWS environment.
It is recommended that these variables be encrypted with Ansible Vault.  See https://docs.ansible.com/ansible/2.4/ansible-vault.html for details.*

aws_ec2_aws_access_key: ABCDEFGHI
aws_ec2_aws_secret_key: ABCDEFGHI

**AWS Region**

*The region in which to create the EC2 instance*

aws_ec2_region: us-east-1

**EC2 Instance Attributes**

*The name of the EC2 instance*

aws_ec2_name: MyEC2Instance

*The ami image id for the EC2 instance*

aws_ec2_image: ami-bb9a6bc2

*The subnet for the EC2 instance*

aws_ec2_subnet: sub_public_a

*The keypair to use for the EC2 instance*

aws_ec2_key: mykey

*The instance type for the EC2 instance*

aws_ec2_instance_type: t2.micro

*A list of security groups for this EC2 instance*

aws_ec2_security_groups:

aws_ec2_user_data:

**Tags**

*The value to use for the Project tag*

aws_ec2_tag_project: MyProject

**DNS Information**

*If you wish to register a private DNS name for this EC2 instance
set aws_ec2_create_dns to True*

aws_ec2_create_dns: False

*If aws_ec2_create_dns is True, the name of the DNS zone (optional)*

aws_ec2_dns_domain: example.com

**Ansible Groups**

*A list of ansible groups to add this host to (optional)*

aws_ec2_ansible_groups:

The role includes no variables (vars).
The role does not depend on any global variables or variables from other roles.

Dependencies
------------------

This role does not depend on any other Ansible roles.

Example Playbook
----------------

The following is a simple example of how you might use this role.

    - hosts: localhost
      connection: local
      gather_facts: False
      tasks:
      - include_role:
          name: level27tech.aws_ec2
      vars:
          aws_ec2_aws_access_key: "AVIBI4QDEWFZOC2T3K4A"
          aws_ec2_aws_secret_key: "Br9t-/gEN+OYfrbDmr7f63NyliCPIrDvTdcTUMHf"
          aws_ec2_region: "us-east-1"
          aws_ec2_subnet: "MySubnet"
          aws_ec2_name: "MyEC2Instance"
          aws_ec2_key: MyKeyPair
          aws_ec2_image: ami123456
          aws_ec2_security_groups:
          - "my_security_group"
          
License
----------

GPLv3.0

Author Information
---------------------------

Name: Dean Harris

Organisation: Level 27 Technology Ltd
