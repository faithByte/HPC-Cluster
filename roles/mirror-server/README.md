# Mirror Server 

Mirror Server or:

- **YUM/DNF** repository server
- **APT** repository server

It mirrors upstream repos using tools like reposync, apt-mirror, or rsync

## Why we need it in a cluster?

### Problem
- Only master node has Internet access

- Worker nodes cannot reach public repositories

- Workers still need:

	- OS updates
	- Security patches
	- Consistent package versions

### How it solves this

- Downloads entire repositories

- Stores them locally on the master

- Lets workers use the master as a local repository


```
				          Internet
				 	         |
				  ┌──────────▼──────────┐
				  │        MASTER       │
				  │ apt-mirror/reposync │
				  │        Nginx        │
  				  └──────────┬──────────┘
							 |
				 ┌───────────┼───────────┐
				 │           │           │
			┌────▼────┐ ┌────▼────┐ ┌────▼────┐
			│ Worker1 │ │ Worker2 │ │ Worker3 │
			│ apt/dnf │ │ apt/dnf │ │ apt/dnf │
			└─────────┘ └─────────┘ └─────────┘
```