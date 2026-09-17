# Hyper-V Enterprise Infrastructure Lab

This is my home lab, built using Hyper-V running on an old Dell OptiPlex I had lying around. I'm using it to build and break an IT infrastructure and move beyond theory, as part of studying for my Network Administration / Cybersecurity Associate degrees.

The plan is to start small, a couple of VMs talking to each other, and keep adding on to it — more servers, routing, Linux, containers, monitoring, whatever I need to learn next. I'm using this repo to track what I build and to document the stuff that breaks along the way, since troubleshooting is honestly the part I learn the most from.

## Hardware

- Dell OptiPlex 3060 SFF
- Intel Core i5-8500
- 16 GB RAM
- 500 GB storage
- 1 physical NIC

Not a lot to work with, so I'm designing around these limits for now. If I hit a wall then I'll upgrade when I need to.

## What I'm trying to learn

Some of this I already know, some I don't — that's kind of the point of the lab:

- Hyper-V and virtual networking
- IPv4/IPv6, routing, NAT
- DNS/DHCP
- Firewalls and segmentation
- Active Directory / Windows Server
- Linux basics
- Docker / container networking
- VLANs
- Wireshark
- PowerShell and Bash scripting
- Monitoring/logging
- Eventually: Ansible, VPNs, backups, maybe some cloud stuff

This list will probably change a lot as I go.

## How I'm approaching it

I'm building this in stages instead of trying to plan out the whole network up front — partly because I don't fully know what I want yet, and partly because figuring out the design as new requirements come up is a big part of what I'm trying to learn.

I'm also planning to break things on purpose sometimes, not just document accidents. When something breaks (on purpose or not), I'll try to work through it properly instead of just fixing it and moving on:

1. Notice something's wrong
2. Write down what I'm seeing
3. Guess why
4. Test the guess
5. Make a change
6. Check if it actually worked
7. Write it up

## Repo layout

Docs, diagrams, scripts, and any troubleshooting write-ups will live in this repo as I go — I'll add folders as they're actually needed rather than scaffolding everything up front. No VM disks, ISOs, or credentials will ever be committed here.

## Where things stand now

The host and repository are set up, and two temporary VMs can communicate on the client-side virtual switch. I'm finishing the Phase 1 packet captures and troubleshooting test before moving on to the firewall VM. Each phase has its own README with the setup, results, and screenshots. Full task-level tracking is in [`NetLabz_Project_Checklist.xlsx`](NetLabz_Project_Checklist.xlsx) — currently planning **Phase 2 of 21**.

| Phase | Status | Summary |
|---|---|---|
| [0 — Planning / Baseline](docs/phase_0/README.md) | [X] Complete | Host baseline, repo setup, naming/addressing/switch standards |
| [1 — Virtual Switching & Test Network](docs/phase_1/README.md) | [X] Complete | Virtual switches + test VMs communication |
| 2 — Firewall / Routing | [] In Progress | — |


**Next up:** Choose and build the firewall VM, then use it to connect the lab networks under controlled rules.