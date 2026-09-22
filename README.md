# ISEA Bridging 2026 – Lab Progress

Introduction to Server Environments and Architectures (Kaplan / Murdoch).
Environment: VMware Workstation, Ubuntu VM. AWS EC2 (Singapore) and Azure for Students for cloud labs.

## Progress

| Lab | Topic | Status |
|-----|-------|--------|
| 1a-1 | Virtualisation & Linux setup | Done |
| 1a-2 | CLI familiarisation | Done |
| 1b | Linux services – Apache | Done |
| 2a | TCO comparison | To do |
| 2b | Cloud VM + bash scripting | To do |
| 3a / 3b | | To do |
| 4a / 4b | | To do |
| Extra | Additional server service | To do |

---

## Lab 1a-1 – Virtualisation & Linux setup
Installed Ubuntu in VMware Workstation and booted to the desktop.

![VMware Ubuntu desktop](lab1a-1-virtualisation/01-vmware-ubuntu-desktop.png)

**Issue:** [add: password lockout, VM rebuild, what you learned]

---

## Lab 1a-2 – CLI familiarisation
Commands used: `touch`, `nano`, `cat`, `cp`, `mv`, `ls -la`, `uname -a`, `whoami`, `sudo`.

| Step | Screenshot |
|------|-----------|
| Create file and open in nano | ![](lab1a-2-cli/01-touch-and-nano-open.png) |
| nano warned the file was already open in another session | ![](lab1a-2-cli/03-nano-already-open-warning.png) |
| Typed content and saved | ![](lab1a-2-cli/05-nano-saved-wrote-1-line.png) |
| `cat`, `cp`, then a `mv` typo (`test file3` instead of `testfile3`) gave an error | ![](lab1a-2-cli/06-cat-cp-mv-typo-error.png) |
| Corrected `mv`, confirmed with `ls -la` | ![](lab1a-2-cli/07-mv-fixed-ls-la.png) |
| `uname -a`, `whoami`, `sudo whoami` | ![](lab1a-2-cli/08-uname-whoami-sudo.png) |

**Note:** [add ps and top screenshots]

### Troubleshooting: VM lost network access
`apt update` failed with "Temporary failure resolving", and `ping 8.8.8.8` returned "Destination Host Unreachable" / "No route to host". Network connectivity was restored later and `apt update` then worked.

| Step | Screenshot |
|------|-----------|
| `apt update` DNS failure | ![](lab1a-2-troubleshooting-network/01-apt-update-dns-failure.png) |
| `ping` unreachable | ![](lab1a-2-troubleshooting-network/02-ping-destination-host-unreachable.png) |
| `ping` no route to host | ![](lab1a-2-troubleshooting-network/03-ping-no-route-to-host.png) |
| `ping` restored (0% loss) | ![](lab1a-2-troubleshooting-network/04-ping-restored.png) |
| `apt update` working | ![](lab1a-2-troubleshooting-network/05-apt-update-success.png) |

**Fix:** [add what you did to restore the network, e.g. VMware network adapter setting / reconnect]

---

## Lab 1b – Linux services: Apache
```
sudo apt install -y apache2
sudo apt install curl
curl 127.0.0.1
sudo service apache2 status
```

| Step | Screenshot |
|------|-----------|
| Install Apache | ![](lab1b-apache/01-apache-install.png) |
| Install complete; `curl` was missing | ![](lab1b-apache/02-apache-installed-curl-missing.png) |
| Installed curl, "Apache2 Ubuntu Default Page: It works" | ![](lab1b-apache/03-curl-installed-it-works.png) |
| Service active (running) | ![](lab1b-apache/04-apache-service-status-running.png) |

The status log shows a harmless warning that the server's fully qualified domain name could not be determined, so it defaulted to 127.0.1.1. Setting `ServerName` in the Apache config removes it.

---

## Lab 2 onwards
To be added.
