---
title: Run a script on boot
---

Systemd is the default init system for most modern Linux distributions, including Raspberry Pi OS. You can use systemd to run a script (bash, python, or other) on boot.

Create a new service file in `/etc/systemd/system/`:

```bash
sudo nano /etc/systemd/system/myscript.service
```

Add the following content to the file:

```
[Unit]
Description=My Script
After=network.target

[Service]
Type=simple
User=pi
WorkingDirectory=/home/pi/server
ExecStart=/home/pi/server/venv/bin/python /home/pi/server/script.py
Restart=always

[Install]
WantedBy=multi-user.target
```

You will need to make some changes to the above file:

- `Description` - A description of the service.
- `After` - The service will start after the network is up.
- `WorkingDirectory` - The directory where the script is located.
- `ExecStart` - The command to run. In this case, it is a Python script and a virtual environment is used.

Save the file and exit the editor.

Enable and start the service:

```bash
sudo systemctl enable myscript.service
sudo systemctl start myscript.service
```

Check the status of the service:

```bash
sudo systemctl status myscript.service
```
