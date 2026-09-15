# Virtual Switches
Hyper-V uses virtual switches to control how virtual machines communicate with each other, the host, and external networks. There are three main switch types: External, Internal, and Private.

## External
An external switch connects Virtual Machines to a physical network adapter. Imagine your plugging a VM into the same physical switch your host is connected to.

External Switches can usually:
    - Access the internet
    - Devices on LAN
    - Communicate with other VM's 
    - Communicate with Hyper-V host

## Internal Switch
An Internal switch allows communication between virtual machines and the Hyper-V host, but does not connect directly to the physical network.

This allows:
    - VM-to-VM communication
    - VM-to-host communication

It does not provide internet or physical LAN access unless routing or NAT is configured separately.


Internal switches are useful for isolated lab networks because the host can still manage and troubleshoot the virtual machines without exposing them directly to the physical network.

<b>*This will be the primary switch type used for internal lab subnets.*

## Private Switch
A Private switch provides the highest level of isolation. Only virtual machines connected to the same Private switch can communicate with each other. The Hyper-V host and physical network cannot directly access the VMs on this switch.

# Planned Use of Switches
The lab will primarily use a combination of External and Internal switches.

The External switch will provide connectivity between the virtual firewall and the physical network, while Internal switches will be used to separate lab networks such as servers, clients, management systems, and DMZ resources.

This design allows the lab to access external resources while keeping internal virtual machines separated from the home network and placing routing and firewall decisions under lab control.

## Virtual Switches Planned to Use
- vSW-EXT
- vSW-SERVER 
- vSW-CLIENT
- vSW-DMZ
- vSW-MGMT