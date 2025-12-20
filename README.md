# HPC Cluster

This project automates the setup of an HPC cluster using Ansible.

## Requirements

* Proper hostnames and networking in place
* Ansible (controller machine)
* SSH access to all nodes
* Python available on managed hosts


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

## Roles

This project is organized around **Ansible roles**, each responsible for one concern.

| Feature            | RedHat        | Debian        |
|:------------------:|:-------------:|:-------------:|
| nginx server       | ✓             | ✓             |
| Mirror server      | ✓             | ✓             |
| Mirror client      | ✓             | ✓             |
| DNS server         |               |               |
| DNS client         |               |               |
| NFS server         |               |               |
| NFS client         |               |               |
| Slurmd             |               |               |
| Slurmctl           |               |               |
| Slurmdb            |               |               |
| Kubernetes cluster |               |               |
| Xcat               |               |               |
| LDAP server        |               |               |
| LDAP client        |               |               |

---

