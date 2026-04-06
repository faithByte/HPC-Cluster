# HPC Cluster

An Ansible-powered project that automates the creation of a fully functional HPC cluster — from bare nodes to parallel-ready in minutes.

## Requirements

* Proper hostnames and networking in place
* Ansible (controller machine)
* SSH access to all nodes
* Python available on managed hosts

## Architecture Overview

This setup is designed around a multi-node architecture managed via Ansible, consisting of a single master node and multiple worker nodes.

```

				       USER
				 	     |
				  ┌──────▼──────┐
				  │    MASTER   │
  				  └──────┬──────┘
					     |
			 ┌───────────┼───────────┐
  			 │           │           │
		┌────▼────┐ ┌────▼────┐ ┌────▼────┐
		│ Worker1 │ │ Worker2 │ │ Worker3 │
		└─────────┘ └─────────┘ └─────────┘

```

> Offline workers friendly setup

## Node Roles

### Master node

- Acts as the control node

- Has internet access

- Runs Ansible and orchestrates configuration and deployment

- Connects to all worker nodes over an internal network

### Worker nodes

- Have no direct internet access

- Are reachable only through the internal network

- Receive all configuration, packages, and updates via the master node

## Supported Operating System Setups

The Ansible roles are written to support two deployment scenarios:

### 1. Mixed RHEL-based Setup

Master: RHEL 9

Workers: Rocky Linux 9

### 2. Debian-based Setup

Master: Debian 12

Workers: Debian 12

## Roles

This project is organized around **Ansible roles**, each responsible for one concern.

| Feature            | RedHat        | Debian        |
|:------------------:|:-------------:|:-------------:|
| nginx server       | ✓             | ✓             |
| Mirror server      | ✓             | ✓             |
| Mirror client      | ✓             | ✓             |
| DNS server         | ✓             | ✓             |
| DNS client         | ✓             | ✓             |
| NFS server         | ✓             | ✓             |
| NFS client         | ✓             | ✓             |
| Slurmd             | ✓             | ✓             |
| Slurmctl           | ✓             | ✓             |
| Slurmdb            |               |               |
| Kubernetes cluster | ✓             | ✓             |
| Xcat               |               |               |
| LDAP server        |               |               |
| LDAP client        |               |               |

---

