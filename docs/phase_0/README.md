# Phase 0 - Lab Planning and Baseline

Before touching any virtual infrastructure, I spent Phase 0 documenting the host, deciding on naming/addressing standards, and planning how the virtual networks would be split up. Nothing was actually deployed yet — this was all groundwork so I wouldn't be making naming and IP decisions on the fly once VMs started piling up.

## Host Baseline

The lab runs on a physical machine I named `NETLABZ`.
At the beginning of the project, the host baseline included:

- Intel Core i5-8500
- 6 physical cores / 6 logical processors
- 16 GB RAM
- Samsung 970 EVO 500 GB SSD
- Realtek 1 GbE physical network adapter
- Hyper-V virtual networking

The full output and screenshots are documented in:

[Host Baseline](host_baseline.md)

## Naming Standard

I set a naming convention before building anything so systems get named by role instead of me making it up as I go

Examples include:

| Object | Standard | Example |
|---|---|---|
| Hyper-V Host | `HYPV##` | `HYPV01`, `HYPV02` |
| Firewall / Router | `FW##` | `FW01`, `FW01` |
| Domain Controller | `DC##` | `DC01`, `DC02` |
| Windows Server | `ROLE##` | `FILE01`, `APP01`, `WEB01` |
| Windows Client | `CLIENT##` | `CLIENT01` |
| Linux Server | `LXSRVR##` | `LXSRVR01` |
| Virtual Switch | `vSW-ROLE` | `vSW-SERVER` |

This gives the environment a consistent naming structure that can continue to scale as additional systems are added.

[Naming Standard](naming_standard.md)

## IP Address Plan

I split the lab into `/24` networks under `10.10.0.0`, one per function:

| Network | Subnet | Planned Gateway |
|---|---|---|
| Server | `10.10.10.0/24` | `10.10.10.1` |
| Client | `10.10.20.0/24` | `10.10.20.1` |
| DMZ | `10.10.30.0/24` | `10.10.30.1` |
| Management | `10.10.40.0/24` | `10.10.40.1` |
| Monitoring | `10.10.50.0/24` | `10.10.50.1` |
| Security | `10.10.60.0/24` | `10.10.60.1` |
| Containers | `10.10.70.0/24` | `10.10.70.1` |

And a consistent range breakdown inside each subnet:

- `.1` - Default gateway
- `.2 - .9` - Network infrastructure
- `.10 - .29` - Servers
- `.30 - .49` - Management / infrastructure
- `.50 - .99` - Reserved / static addressing
- `.100 - .199` - DHCP clients
- `.200 - .239` - Lab / testing

[IP Address Plan](ip_address_plan.md)

## Virtual Network Design

I'm mostly going to use **Internal switches** for the lab networks — VMs and the host can talk to each other without any of it touching my home network. An **External switch** will handle the connection between the virtual firewall and the physical network (NIC) once that's built.

Planned switches:

| Switch | Purpose |
|---|---|
| `vSW-EXT` | External / physical network connectivity |
| `vSW-SERVER` | Server network |
| `vSW-CLIENT` | Client network |
| `vSW-DMZ` | DMZ resources |
| `vSW-MGMT` | Management network |

Routing between these will be handled by the firewall VM later, not by the switches themselves.

[Virtual Switch Design](virtual-switches.md)

## Where Phase 0 leaves things

By the end of this phase I had the host documented, a naming convention, an IP plan, and a rough network design — all before spinning up a single VM. Phase 1 is where I actually start building on top of this.