# The Panicled infrastructure as code repo

## Goals:

- Experiment with virtualisation, continuous integration, containers and infrastructure as code.
- Initial technologies: CentOS, kickstart, KVM, Docker, Salt, netdata
- Have a complete lab that can rebuild itself from version-controlled sources
- Allow feature flags to enable/disable lab components and control configuration
- Document the process so that maximum learning is achieved and others may benefit
- *Stretch goal*: set up dev/uat/prod environments


## First stage:

Enable installation of a bootstrap server onto a laptop

- minimal install of a known version of CentOS
- script to set up a standalone Salt master
- pull down a repo of Salt configs
- apply configs to enable:
- DHCP server
- tftp server
- yum repo server
- CentOS data from DVD image
- maybe a local repo for custom packages

Resources:

- [Minimal installation](https://www.centos.org/forums/viewtopic.php?t=47262) for a 1GB stick?
- [cisco complete-kickstart-how-to-save-time-installing-linux](https://www.linuxtoday.com/blog/complete-kickstart-how-to-save-time-installing-linux.html)
- [centoscreating-kickstart-files](https://docs.centos.org/en-US/8-docs/advanced-install/assembly_creating-kickstart-files/)
- [redhat kickstartconfig](https://access.redhat.com/labs/kickstartconfig/)
- [local-http-yum-repository](https://www.tecmint.com/setup-local-http-yum-repository-on-centos-7/)


## Second stage:

Install the bare metal hypervisors

- PXE boot each machine using the laptop as source
- install OS from served kickstart
- install Salt masterless on these machines
- pull down this machine's Salt config repo
- machine configures itself

Resources:

- [reddit advice_on_getting_experience_with_automation](https://www.reddit.com/r/homelab/comments/6612r1/advice_on_getting_experience_with_automation/)
- [CentOS 8 server setup](https://www.tecmint.com/initial-server-setup-with-centos-rhel-8/)


## Third stage:

Deploy the VMs with dummy data (assume that in prod, all data directories would be mounted from a NAS/SAN).

- could be terraform
- could be Salt alone
- could be Kubernetes, just for extra fun

Resources:

- [ionos use-terraform-and-saltstack](https://devops.ionos.com/tutorials/use-terraform-and-saltstack-for-provisioning-and-configuration-management/)
- [reddit dipping_my_toes_into_the_world_of](https://www.reddit.com/r/sysadmin/comments/cqkd00/advice_for_dipping_my_toes_into_the_world_of/)
- [reddit terraform_repo_structure_best_practice](https://www.reddit.com/r/devops/comments/dbtn78/terraform_repo_structure_best_practice/)

