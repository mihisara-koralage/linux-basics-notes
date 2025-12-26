# Day 11 – Package Management with APT

## What is a Package Manager?
A package manager is a tool that installs, updates, and removes software on a Linux
system. It also handles software dependencies automatically.

Ubuntu uses the **APT (Advanced Package Tool)** package manager.

Package managers help ensure software is installed safely and consistently.

---

## Why Package Management is Important in DevOps
In DevOps environments, servers are set up and configured frequently.
Package management is important because it:
- Automates software installation
- Ensures correct dependencies are installed
- Keeps systems up to date and secure
- Helps maintain consistent server environments

Most server setup and automation scripts rely on package managers.

---

## Updating the Package List
Before installing any software, the package list should be updated.

Command used:

- sudo apt update : This command fetches the latest information about available packages.

##Installing Packages

- sudo apt install curl : Software can be installed using the apt install command.
- curl --version : Verify installation
 
##Upgrading Installed Packages
Installed packages can be upgraded to newer versions.

- sudo apt upgrade : This updates all installed packages to their latest versions.

##Removing Packages
Packages can be removed when no longer needed.

- sudo apt remove curl 
- sudo apt purge curl : Remove package and configuration files

##Searching for Packages
Before installing software, packages can be searched.

- apt search nginx : This helps identify available packages in the repository.

##Practical Commands Used

```sudo apt update
sudo apt install curl
curl --version
sudo apt upgrade
sudo apt remove curl
sudo apt install tree
tree```

##What I Practiced
- Updating package lists
- Installing and removing software
- Searching for available packages
- Understanding the role of package management in DevOps



