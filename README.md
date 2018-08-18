# Centos Atomic Vagrant Configurations for Openshift Origin

Should provide a starting point to create an Openshift Origin cluster on Centos Atomic.

## Prerequisites

- Get the latest Centos Atomic Vagrant image from cloud.centos.org (https://cloud.centos.org/centos/7/atomic/images/)
  - Import the image into vagrant
  ```
  vagrant box add --name centos_atomic_7 CentOS-7-x86_64-Vagrant-1801_02.VirtualBox.box
  ```
- Generate SSH keys for your vagrant environment
  - place these files as 'id_rsa' and 'id_rsa.pub' in the working directory
  ```
  ssh-keygen -f ./id_rsa
  ```
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
ansible-playbook ~/ansible/openshift-ansible/playbooks/prerequisites.yml
ansible-playbook ~/ansible/openshift-ansible/playbooks/deploy_cluster.yml 
```

If all is well you should see:

```
PLAY RECAP ****************************************************************************************************************************************************************************************************************************************************
localhost                  : ok=13   changed=0    unreachable=0    failed=0   
master                     : ok=558  changed=227  unreachable=0    failed=0   
node-a                     : ok=119  changed=41   unreachable=0    failed=0   
node-b                     : ok=119  changed=41   unreachable=0    failed=0   


INSTALLER STATUS **********************************************************************************************************************************************************************************************************************************************
Initialization             : Complete (0:00:45)
Health Check               : Complete (0:00:39)
etcd Install               : Complete (0:02:32)
Master Install             : Complete (0:04:56)
Master Additional Install  : Complete (0:01:08)
Node Install               : Complete (0:06:12)
Hosted Install             : Complete (0:04:22)
Web Console Install        : Complete (0:01:22)
Service Catalog Install    : Complete (0:04:01)
```

## Cleanup
Unless more playbooks need to be run, the manager node can be shutdown to save on resources. 
