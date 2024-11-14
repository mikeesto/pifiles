---
title: APT timing out
---

APT defaults to IPv6 when it is available, and in some cases it does not seem to play nicely in corporate networks. Typically what happens is that a repository like `archive.raspberrypi.com` times out when running the `atp update` command. The solution - force IPv4 instead.

You can do this via the `-o` flag when running the command:

```bash
sudo apt -o Acquire::ForceIPv4=true update
```

Or you can edit the apt configuration and add a line to make IPv4 permanent:

```bash
sudo nano /etc/apt/apt.conf.d/99force-ipv4
```

Add this line:

```bash
Acquire::ForceIPv4 "true";
```
