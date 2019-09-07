vpc-role
=========

A simple Ansible role to create AWS VPC setup.

Pending tasks
------------
NA

Role Variables
--------------

While creating "vpc_network_map_pub/pvt", please make sure to add the format with "aws_occ".

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

MIT

Author Information
------------------

Author: Manoj Chandran

Email: manoj.meparambu@gmail.com

Please send support requests, bug reports or feature proposals via Github.

------------------
