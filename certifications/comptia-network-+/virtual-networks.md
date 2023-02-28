# Virtual Networks

For example to create 10 virtuals servers inside 1 physical machine. We need to create a virtual networks.&#x20;

## Network function virtualization (NFV)&#x20;

In order to replace physical network devices with the virtual version, we need NFV.&#x20;

* It will be manage from the hypervisor
* Same functionnality as a physical device (Ex: routing, switching, load balancing, firewalls, etc...)
* Quickly and easily deploy from hypervisor
* Many different deployment options

So what is the **hypervisor** ?

* It is a virtual machine manager (VMM), who manages all other virtual machine, virtual networks
* &#x20;It can manage the hardware like : CPU, Networking,Security of each virtual machine
* All in one screen

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

1. Virtual Network
2. Virtual Machine
3. Hardware management

### Virtual Switch

* Once we created a VM, we need to link all of them. So need the vSwitch
* It have a same functionality of a physical switch
  * Forwarding options
  * Links aggregation
  * Port mirroring
  * Netflow
* Quick deploy or remove with  the hypervisor

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### Virtual Network Interface Card (vNIC)

In order to communicate with the internet, we need the vNIC

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
