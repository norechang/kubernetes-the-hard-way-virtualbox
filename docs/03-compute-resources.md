# Provisioning Compute Resources

Kubernetes requires a set of machines to host the Kubernetes control plane and the worker nodes where containers are ultimately run. In this lab you will provision the compute resources required for running a secure and highly available Kubernetes cluster.


## Networking

The Kubernetes [networking model](https://kubernetes.io/docs/concepts/cluster-administration/networking/#kubernetes-model) assumes a flat network in which containers and nodes can communicate with each other. In cases where this is not desired [network policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) can limit how groups of containers are allowed to communicate with each other and external network endpoints.

Each machine uses two network interface, one for access the Internet with type "NAT", the other for Kubernetes internal communication with type "Host-only Adapter".


## Compute Instances

The compute instances in this lab will be provisioned using [Ubuntu Server](https://www.ubuntu.com/server) 16.04, which has good support for the [cri-containerd container runtime](https://github.com/kubernetes-incubator/cri-containerd). Each compute instance will be provisioned with a fixed private IP address to simplify the Kubernetes bootstrapping process.

### Fire up VMs w/ Vagrant

```
vagrant up
```

> output

```
Bringing machine 'controller-0' up with 'virtualbox' provider...
Bringing machine 'controller-1' up with 'virtualbox' provider...
Bringing machine 'controller-2' up with 'virtualbox' provider...
Bringing machine 'worker-0' up with 'virtualbox' provider...
Bringing machine 'worker-1' up with 'virtualbox' provider...
Bringing machine 'worker-2' up with 'virtualbox' provider...
Bringing machine 'worker-3' up with 'virtualbox' provider...
Bringing machine 'worker-4' up with 'virtualbox' provider...
...
...

```

### Summary
List the compute instances:

```
vagrant status
```

> output
```
controller-0              running (virtualbox)
controller-1              running (virtualbox)
controller-2              running (virtualbox)
worker-0                  running (virtualbox)
worker-1                  running (virtualbox)
worker-2                  running (virtualbox)
worker-3                  running (virtualbox)
worker-4                  running (virtualbox)
```

## Kubernetes Master VIP
Adopting `heatbeat` service to establish a VIP: "10.240.0.100" as the entrance to the controller cluster.

### Verify
```
ping -c 1 10.240.0.100
```

> output

```
PING 10.240.0.100 (10.240.0.100): 56 data bytes
64 bytes from 10.240.0.100: icmp_seq=0 ttl=64 time=0.438 ms

--- 10.240.0.100ping statistics ---
1 packets transmitted, 1 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.438/0.438/0.438/0.000 ms
```

Next: [Provisioning a CA and Generating TLS Certificates](04-certificate-authority.md)
