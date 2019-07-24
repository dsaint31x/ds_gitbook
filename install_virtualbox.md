# Install Virtualbox on Ubuntu18.04

## Test Env.
* Ubuntu 18.04

## Setup APT Repository

```
sudo apt update
sudo apt upgrade
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"
```
* This command will add an entry to /etc/apt/sources.list at end of the file.

## Install

```
sudo apt update
sudo apt install virtualbox-6.0
```

## References

* [TecAdmin.net](https://tecadmin.net/install-virtualbox-on-ubuntu-18-04/)