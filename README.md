# Red Hat Delivery Specialist - Ansible Advanced - Final Lab

* From the cloned repo run `site-config-tower.yml` playbook to create job templates and workflow template.

## List of Playbooks

| Playbook | Description | Roles | Description |
| -------- | ----------- | ----- | ----------- |
| `site-setup-prereqs.yaml` | Setup OSP workstation & core resources | 1. `setup-workstation` | Setup workstation with SSH keypair & required software
| | | 2. `osp-setup` | Provision OSP network, security groups, keypair, image, flavors
| `site-install-isolated-node.yaml` | Install Ansible Tower on isolated node | TODO |
| `site-config-tower.yml` | Configure Ansible Tower | `config-tower` | Configure Tower project, inventories, job templates and workflow
| `site-osp-instances.yml` | Provision OSP instances | `osp-servers` | Create OSP server instances
| `aws_provision.yml` | Use `order_svc.sh` script to provision env | TODO |
| `aws_creds.yml` | Fetch GUIDkey.pem from bastion of Three tier application env and create machine credential to connect to AWS instances | TODO |
| `aws_status_check.yml` | Check aws instances are up or not | TODO |
| `site-3tier-app.yml` | Deploy three tier app | 1. `osp-facts` | Genrate in-memory inventory for OSP instances
| | | 2. `base-config` | Initial, common, system setup steps for all servers
| | | 3. `lb-tier` | Install & configure haproxy load balancer
| | | 4. `app-tier` | Install & configure Apache Tomcat application server
| | | 5. `db-tier` | Install & Configure Postgres database
| `site-smoke-osp.yml` | test three tier app on OSP | None |
| `site-smoketest-aws.yml` | test three tier app on AWS | None |
| `grading-script.yml` | Self grading script | None |
| `site-osp-delete.yml` | Delete OSP instances | `osp-instance-delete` | Delete all OSP server instances
| `site-setup-workstation.yml` | Unused - see `site-setup-prereqs.yaml` instead | setup-workstation | See above |

==== Ansible Tower Config

.List of Playbooks
|===
| roles/config-tower/vars/main.yml | Very important file to review. All the variable values are set there. Please do not make any changes in the file
|===











---

Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

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

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
