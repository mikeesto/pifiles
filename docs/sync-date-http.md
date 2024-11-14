---
title: Sync date & time over HTTP
---

Sometimes the Pi can’t sync its date/time on corporate networks. This is often due to restricted NTP (Network Time Protocol) access. A handy workaround is using `htpdate` instead. Unlike NTP, htpdate syncs time over HTTP by retrieving timestamps from accessible web servers.

First, install htpdate:

```bash
sudo apt install htpdate
```

Often, this will be enough to get the time synced. If not, you can specify a web server to sync from. For example, to sync from Google:

```bash
sudo htpdate -s google.com
```
