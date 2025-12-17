
## Why apt-mirror in a cluster?

### Problem
- Only master node has Internet access

- Worker nodes cannot reach public APT repositories

- Workers still need:
  - OS updates
  - Security patches
  - Consistent package versions

### How apt-mirror solves this

- Downloads entire APT repositories (or selected ones)

- Stores them locally on the master

- Lets workers use the master as a local APT repository

- Ensures:

  - Isolation (still no Internet on workers)

  - Reproducibility (same packages everywhere)

  - Centralized control

In cluster environments (HPC, HA, Kubernetes, lab setups), this is a standard pattern.

```
				     Internet
				 	     |
				  ┌──────▼──────┐
				  │    MASTER   │
				  │  apt-mirror │
				  │    Nginx    │
  				  └──────┬──────┘
					     |
			 ┌───────────┼───────────┐
  			 │           │           │
		┌────▼────┐ ┌────▼────┐ ┌────▼────┐
		│ Worker1 │ │ Worker2 │ │ Worker3 │
		│   apt   │ │   apt   │ │   apt   │
		└─────────┘ └─────────┘ └─────────┘
```