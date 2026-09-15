# Network Assignments
Network	        Subnet	        Gateway

Server	        10.10.10.0/24	10.10.10.1
Client	        10.10.20.0/24	10.10.20.1
DMZ	            10.10.30.0/24	10.10.30.1
Management	    10.10.40.0/24	10.10.40.1
Monitoring	    10.10.50.0/24	10.10.50.1
Security	    10.10.60.0/24	10.10.60.1
Containers	    10.10.70.0/24	10.10.70.1


# Within Each Subnet
Address Range       Use
.1                  Default Gateway
.2 - .9             Network Infrastructure
.10 - .29           Servers
.30 - .49           Mgmt / Infrastructure
.50 - .99           Reserved / Static
.100 - .199         DHCP Clients
.200 - .239         Lab / Testing