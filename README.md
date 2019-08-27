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
    ---
    # vars file for vpc-role
    ##############################################
    # AWS Credentials                            #
    ##############################################
    aws_access_key: "THISISMYAWSACCESSKEY"
    aws_secret_key: "ThisIsMyAwSSecretKey"
    aws_region:     "eu-west-1"

    ##############################################
    # VPC Information                            #
    ##############################################
    vpc_name:       "My VPC"
    vpc_cidr_block: "10.0.0.0/16"
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
https://github.com/rcrelia/aws-vpc-scenario2

https://jeremievallee.com/2016/07/27/aws-vpc-ansible.html
