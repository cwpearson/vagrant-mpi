# mpi

Install vagrant

## Quickstart

Bring up the cluster

```
vagrant up
```

Auto-generate some files that are mapped into the master/workers

```
python3 hostfiler.py
```


```
mpirun -n 2 --hostfile /etc/hostfile/hostfile hostname -I
```



## Vagrant

**Box**: a base image to quickly clone a VM

`vagrant box add hashicorp/bionic64`

`vagrant up`: start and provision the vagrant environment
`vagrant destroy`: stop and delete all traces of the 

`vagrant status`: 

`vagrant global-status`: state of all active Vagrant environments for the current user

## Notes
* [Multiple Vagrant VMs in one Vagrantfile](https://www.thisprogrammingthing.com/2015/multiple-vagrant-vms-in-one-vagrantfile/)
* [Linked Clone](https://www.vagrantup.com/docs/virtualbox/configuration.html#linked-clones)