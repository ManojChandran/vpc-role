vpc-role
=========

A simple Ansible role to create AWS VPC setup.
This role provides:

  a VPC across two AZs
  an Internet gateway and adds to VPC
  a public and a private subnet in each AZ


Pending tasks
------------
Need to check on how to pass variable vpc_id with different task YAML files
Need to check on the origin and definition of the variable aws_env



Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the

```
    # vars file for vpc-role
    ####################################################
    # AWS Credentials                                  #
    ####################################################
    aws_region:     "us-east-1"

    ####################################################
    # VPC Information                                  #
    ####################################################
    vpc_name:       "My VPC"
    #vpc_name: "vpc-{{ aws_env }}"
    vpc_cidr_block: "10.0.0.0/16"

    ####################################################
    # AZ's, Subnets and CIDR's                         #
    ####################################################
    vpc_network_map_pub:
      # public subnet
      - { aws_occ: 0, aws_az: "{{ aws_region }}a", aws_az_cidr: "10.0.0.0/24" }
      - { aws_occ: 1, aws_az: "{{ aws_region }}b", aws_az_cidr: "10.0.2.0/24" }

    vpc_network_map_pvt:
        # private subnet
      - { aws_occ: 0, aws_az: "{{ aws_region }}a", aws_az_cidr: "10.0.1.0/24" }
      - { aws_occ: 1, aws_az: "{{ aws_region }}b", aws_az_cidr: "10.0.3.0/24" }

    ####################################################
    # Access location CIDR defs (used in NACLs and SGs)#
    ####################################################
    public_cidr: "0.0.0.0/0"

    ####################################################
    # security group parameters                        #
    ####################################################
    private_sg_name: "PrivateSecurityGroup"
    public_sg_name:  "PublicSecurityGroup"
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

Author: Manoj Chandran

Email: manoj.meparambu@gmail.com

------------------
