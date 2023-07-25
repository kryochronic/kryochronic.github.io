---
layout: post
title:  "Expose Windows Docker Daemon on WSL2 to External Hosts or Other VMs"
date:   2022-01-31 23:06:00 +0530
categories: jekyll update
---

# Expose Windows Docker Daemon on WSL2 to External Hosts or Other VMs

This took me a few hours to figure out so I hope it helps some one.
My setup
```
          Host                                 Guest
    +-----------------+                  +-----------------+
    |                 |       NAT        |                 |
    | Docker on Win11 |  <------------>  | Ubuntu Linux VM |
    |     WSL 2       |   192.168.15.x   |                 |
    |                 |                  |                 |
    +-----------------+                  +-----------------+
      192.168.4.61                          192.168.15.128
  (assigned by my router)
      
      192.168.15.1
  (assigned by VNAT on my machine)

```

## Solution
Since Docker employs WSL2 here, which by default binds to 127.0.0.1,
you may want to fire the below as an admin on Windows PowerShell
```
netsh interface portproxy add v4tov4 listenport=2375 listenaddress=<your-public-ip> connectaddress=127.0.0.1 connectport=2375
```

* You should replace `listenaddress=<your-public-ip>` block with the IP of your accessible address.
* If you need the Daemon to be avaialable from the external network, say `listenaddress=192.168.4.61`.
* I set it to `listenaddress=0.0.0.0`
* Also, you'll need to allow port `2375` through the Win11-firewall if you actually want machines on your network to access this daemon on the Win11 Machine.
* Ofcourse dont forget to set `DOCKER_HOST` in the Guest OS
  * `export DOCKER_HOST=tcp://192.168.15.1` in my case, linux ( Ubuntu)
  * `set DOCKER_HOST=tcp://192.168.15.1` For Win based guest OSs on the commandline, or set it as the `Environment Variable` from System Settings.
    * Don't forget to spawn a new CMD / PS window, since the new Environment Variables till you restart the shell.

## References
[StackOverflow - Answer](https://stackoverflow.com/questions/60151451/how-to-expose-2375-from-docker-desktop-for-windows)