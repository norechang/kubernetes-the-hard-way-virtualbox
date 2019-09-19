# Prerequisites

## VirtualBox

This tutorial leverages the [VirtualBox](https://www.virtualbox.org/) to streamline provisioning of the compute infrastructure required to bootstrap a Kubernetes cluster from the ground up. Click to [download and install VirtualBox](https://www.virtualbox.org/wiki/Downloads).

## Vagrant

Leverage [Vagrant](https://www.vagrantup.com/) for vm management, and adopting [vagrant-hosts](https://github.com/oscar-stack/vagrant-hosts) to manage '/etc/hosts' among vms.

```
vagrant plugin install vagrant-hosts
```

> output

```
Installing the 'vagrant-hosts' plugin. This can take a few minutes...
Installed the plugin 'vagrant-hosts (2.8.0)'!
```

## Get a clone of this repository and use the repositroy root as working directory

```
git clone https://github.com/norechang/kubernetes-the-hard-way-virtualbox.git
```

Next: [Installing the Client Tools](02-client-tools.md)
