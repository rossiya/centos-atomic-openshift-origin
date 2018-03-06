# Centos Atomic Vagrant Configurations for Openshift Origin

Should provide a starting point to create an Openshift Origin cluster on Centos Atomic.

## Prerequisites

- Get the latest Centos Atomic Vagrant image from cloud.centos.org (https://cloud.centos.org/centos/7/vagrant/x86_64/images/)
  - Import the image into vagrant
  ```
  vagrant box add --name centos_atomic_7 CentOS-7-x86_64-Vagrant-1801_02.VirtualBox.box
  ```
- Generate SSH keys for your vagrant environment
  - place these files as 'id_rsa' and 'id_rsa.pub' in the working directory
- Gather any CA Certs you may need for your network 
  - place in ../cacerts/corp.crt relative to working directory



### Running

Run vagrant as normal

```
vagrant up
```

(Optional) Take snapshot before Origin install

```
vagrant snapshot save "preinstall"
```

Then run the openshift-ansible playbook

```
vagrant ssh manager
ansible-playbook ~/ansible/openshift-ansible/playbooks/deploy_cluster.yml 
```
