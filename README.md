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

## Roadmap

* How to modify all the host files once IP addresses are assigned?

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
* [vagrant-hostmanager](https://github.com/devopsgroup-io/vagrant-hostmanager)
* [Running an MPI cluster in a LAN](https://mpitutorial.com/tutorials/running-an-mpi-cluster-within-a-lan/)
* [OpenMPI: Diagnose Multi-Host Problems](https://www.open-mpi.org/faq/?category=running#diagnose-multi-host-problems)
* [Building a Raspberry Pi Cluster: SLURM](https://medium.com/@glmdev/building-a-raspberry-pi-cluster-784f0df9afbd)
