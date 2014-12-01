# Ansible playbook - MEAN stack

The Ansible playbook for this Vagrantfile sets up the [MEAN](http://mean.io/) stack.

### Vagrantfile

* Box used: [Ubuntu 14.04 64-bit (Trusty)](https://vagrantcloud.com/ubuntu/boxes/trusty64)
* [Virtualbox settings:](https://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvm)
 * --memory 1024
 * --natdnshostresolver1 on
 * --natdnsproxy1 on

### Playbook tasks

* Installs build-essential and git packages from Apt.
* MongoDB installation:
 * Imports MongoDB's public GPG key.
 * Adds MongoDB's Apt source.
 * Installs MongoDB
* Node.js installation:
 * Sets up [NodeSource](https://github.com/nodesource/distributions) for Ubuntu.
 * Installed latest version of Node.js.
 * Installs [Grunt](http://gruntjs.com/).
 * Installs the [MEAN](http://mean.io/) stack.
