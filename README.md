# ISEA Bridging 2026 – Lab Progress

Introduction to Server Environments and Architectures (Kaplan / Murdoch).
Environment: VMware Workstation, Ubuntu VM. AWS EC2 (Singapore) and Azure for Students for cloud labs.

## Progress

| Lab | Topic | Status |
|-----|-------|--------|
| 1a-1 | Virtualisation & Linux setup | Done |
| 1a-2 | CLI familiarisation | Done |
| 1b | Linux services – Apache | Done |
| 2a | TCO comparison | Done |
| 2b | Cloud VM + bash scripting | Done |
| 3b | Scripting & cron jobs | Done |
| 4a | Additional server service (MariaDB) | Done |
| 3a | DNS & HTTPS certificates | To do |

---

## Lab 1a-1 – Virtualisation & Linux setup
Installed Ubuntu in VMware Workstation and booted to the desktop.

![VMware Ubuntu desktop](Lab%201/lab1a-1-virtualisation/01-vmware-ubuntu-desktop.png)

**Issue:** [add: password lockout, VM rebuild, what you learned]

---

## Lab 1a-2 – CLI familiarisation
Commands used: `touch`, `nano`, `cat`, `cp`, `mv`, `ls -la`, `uname -a`, `whoami`, `sudo`.

| Step | Screenshot |
|------|-----------|
| Create file and open in nano | ![](Lab%201/lab1a-2-cli/01-touch-and-nano-open.png) |
| nano warned the file was already open in another session | ![](Lab%201/lab1a-2-cli/03-nano-already-open-warning.png) |
| Typed content and saved | ![](Lab%201/lab1a-2-cli/05-nano-saved-wrote-1-line.png) |
| `cat`, `cp`, then a `mv` typo (`test file3` instead of `testfile3`) gave an error | ![](Lab%201/lab1a-2-cli/06-cat-cp-mv-typo-error.png) |
| Corrected `mv`, confirmed with `ls -la` | ![](Lab%201/lab1a-2-cli/07-mv-fixed-ls-la.png) |
| `uname -a`, `whoami`, `sudo whoami` | ![](Lab%201/lab1a-2-cli/08-uname-whoami-sudo.png) |

### More CLI practice: pwd, man, mkdir, ps, top, permissions, find/grep
| Step | Screenshot |
|------|-----------|
| `pwd` | ![](Lab%201/lab1a-2-more-cli/01-pwd.png) |
| `man ls` | ![](Lab%201/lab1a-2-more-cli/02-man-ls.png) |
| `mkdir my lab` typo made two folders instead of one | ![](Lab%201/lab1a-2-more-cli/03-mkdir-typo.png) |
| Corrected `mkdir mylab` | ![](Lab%201/lab1a-2-more-cli/04-mkdir-fixed.png) |
| `touch file1.txt` | ![](Lab%201/lab1a-2-more-cli/05-touch-file.png) |
| `ps` | ![](Lab%201/lab1a-2-more-cli/06-ps.png) |
| `top` | ![](Lab%201/lab1a-2-more-cli/07-top.png) |
| `chmod 755`, `chown`, `find` | ![](Lab%201/lab1a-2-more-cli/08-chmod-chown-find.png) |
| `grep "shalini" /etc/passwd` succeeded after two typo attempts (`/ect/passwd`, `/ect/password`) | ![](Lab%201/lab1a-2-more-cli/09-grep-success.png) |

### Troubleshooting: VM lost network access
`apt update` failed with "Temporary failure resolving", and `ping 8.8.8.8` returned "Destination Host Unreachable" / "No route to host". Network connectivity was restored later and `apt update` then worked.

| Step | Screenshot |
|------|-----------|
| `apt update` DNS failure | ![](Lab%201/lab1a-2-troubleshooting-network/01-apt-update-dns-failure.png) |
| `ping` unreachable | ![](Lab%201/lab1a-2-troubleshooting-network/02-ping-destination-host-unreachable.png) |
| `ping` no route to host | ![](Lab%201/lab1a-2-troubleshooting-network/03-ping-no-route-to-host.png) |
| `ping` restored (0% loss) | ![](Lab%201/lab1a-2-troubleshooting-network/04-ping-restored.png) |
| `apt update` working | ![](Lab%201/lab1a-2-troubleshooting-network/05-apt-update-success.png) |

**Fix:** [add what you did to restore the network, e.g. VMware network adapter setting / reconnect]

---

## Lab 1b – Linux services: Apache

Commands: `sudo apt install -y apache2`, `sudo apt install curl`, `curl 127.0.0.1`, `sudo service apache2 status`

| Step | Screenshot |
|------|-----------|
| Install Apache | ![](Lab%201/lab1b-apache/01-apache-install.png) |
| Install complete; `curl` was missing | ![](Lab%201/lab1b-apache/02-apache-installed-curl-missing.png) |
| Installed curl, "Apache2 Ubuntu Default Page: It works" | ![](Lab%201/lab1b-apache/03-curl-installed-it-works.png) |
| Service active (running) | ![](Lab%201/lab1b-apache/04-apache-service-status-running.png) |

The status log shows a harmless warning that the server's fully qualified domain name could not be determined, so it defaulted to 127.0.1.1. Setting `ServerName` in the Apache config removes it.

---

## Lab 2a – Total Cost of Ownership (TCO) Comparison

Compared a budget inkjet printer against an entry-level laser printer over 5 years, using the lab's default assumptions (750 pages/week, 40 hours/week powered on). Built as an Excel spreadsheet with linked formulas, not hardcoded numbers.

| Step | Screenshot |
|------|-----------|
| TCO comparison spreadsheet with reflection answers | ![](Lab%202/lab2a-tco/01-tco-answers.png) |

**Result:** the laser printer is far cheaper over the 5-year period, despite its higher purchase price, because its running cost per page is much lower — break-even is reached in under 4 weeks at this print volume.

---

## Lab 2b – Cloud VM (AWS EC2) + Bash scripting

Launched a free-tier Ubuntu EC2 instance (t3.micro) in the Asia Pacific (Singapore) region, connected via browser-based SSH (EC2 Instance Connect), updated packages, then wrote and ran a bash script covering `echo`, `for`, `while`, and `if`.

| Step | Screenshot |
|------|-----------|
| Connected to the EC2 instance | ![](Lab%202/lab2b-ec2-bash/01-ec2-connected-terminal.png) |
| `sudo apt update` | ![](Lab%202/lab2b-ec2-bash/02-apt-update-output.png) |
| Wrote `myscript.sh` in nano | ![](Lab%202/lab2b-ec2-bash/03-bash-script-file.png) |
| First run had a `while [$count...]` spacing error | ![](Lab%202/lab2b-ec2-bash/04-bash-script-first-run-error.png) |
| Fixed the spacing, full script ran correctly | ![](Lab%202/lab2b-ec2-bash/05-bash-script-fixed-run.png) |

**What I learned:** small spacing mistakes in bash (missing a space inside `[ ]`) cause real errors, and reading the error message (`command not found`) pointed straight to the problem.

---

## Lab 3b – Scripting & cron jobs

Created a cron job to run a command automatically every minute and log the output to a file:

`* * * * * echo "Cron job ran" >> /home/ubuntu/cronlog.txt`

| Step | Screenshot |
|------|-----------|
| Cron job installed (`crontab -l`) and confirmed running via `cronlog.txt` | ![](Lab%203/lab3b-cron/01-crontab-installed-and-log.png) |

**What I learned:** cron runs scheduled tasks in the background without needing to be logged in, which is how servers automate backups and checks.

---

## Lab 4a – Additional server service: MariaDB

Installed MariaDB, confirmed the service was running, then created and tested a database.

| Step | Screenshot |
|------|-----------|
| MariaDB installed and active (running) | ![](Lab%204/lab4a-mariadb/01-mariadb-status-running.png) |
| Created database `iseatest`, confirmed with `SHOW DATABASES;` | ![](Lab%204/lab4a-mariadb/02-mariadb-create-database-test.png) |

**What I learned:** MariaDB runs as a background service (`systemctl status`) just like Apache, and basic SQL (`CREATE DATABASE`, `SHOW DATABASES`) is enough to confirm a database server works.

---

## Still to do
- Lab 3a – DNS and HTTPS (Let's Encrypt / Certbot) — needs a purchased domain
