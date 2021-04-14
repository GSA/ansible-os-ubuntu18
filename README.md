Ubuntu 18.04 CIS Benchmark
==========================
Configure Ubuntu 18.04 machine to be CIS compliant. Level 1 and 2 findings will be corrected by default. It's based on [CIS Ubuntu Benchmark v2.0.1 - 01-03-2020 ](https://www.cisecurity.org/cis-benchmarks/).


Role Variables
--------------
There are many role variables defined in defaults/main.yml.

##### Hardening will be applied to the following configurations by default:
* General Configurations (Section 1)
* Services Configurations (Section 2)
* Network Configurations (Section 3)
* Logging and Auditing Configurations (Section 4) 
* Access, Authentication and Authorization Configurations (Section 5)
* System Maintenance Configurations (Section 6)

Above high level configurations and other fine-grained configurations can be enabled/disabled using variabled defined in in defaults/main.yml.

##### The configuration will not:
* Install and configure AIDE
* Install and configure NTP
* Configure the /etc/group wheel configurations

Other settings and services are listed. Please review to ensure they meet your organizational requirements.

### Dependencies
Ansible >= 2.7

### Example Playbook

```
---
- name: Harden Server
  hosts: all
  become: yes

  roles:
    - ansible-os-ubuntu18
```

### How to test locally

```
ansible-playbook playbook.yml --connection=local
```
### CircleCI Intergration

This repository has been updated to optionally utilize Continuous Intergration with CircleCI and tests the ansbile tasks against a privledged CentOS-7 Container.  A low number of tasks are incompatiable when ran against a container vs a vm or bare-metal and have ignore_errors turned on.

##### Using CircleCI:
* Fork this repository or create a branch
* Sign up for an account and follow the getting started guide at https://circleci.com/docs/2.0/first-steps/#section=getting-started
* Add the repository to your projects and click start building. https://circleci.com/docs/2.0/project-build/#section=getting-started
* New Commits will trigger the CircleCI build and run the playbook.yml and the result will pass or fail.

### License

BSD.