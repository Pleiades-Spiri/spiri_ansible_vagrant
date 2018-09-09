# Spiri: Ubuntu ROS Kinetic Vagrant Box

This repository contains an Ubuntu ROS Kinetic Vagrant Box box for Vagrant.

## Compatibility & Prerequisites to Install

### Windows

* Tested with VirtualBox 5.2.10: https://download.virtualbox.org/virtualbox/5.2.10/VirtualBox-5.2.10-122406-Win.exe
* Tested with Vagrant 2.1.1: https://releases.hashicorp.com/vagrant/2.1.1/vagrant_2.1.1_x86_64.msi
* Git Bash is highly recommended, not the Windows Command Prompt (cmd.exe): https://git-for-windows.github.io/
    * In Git Bash, click the diamond shaped multi-colored icon in the upper left of the window, OPTIONS. You may want to go through the option list to increase your default window size, set up copy/paste shortcuts, and set up mouse selection for copy/paste.
* On newer machines, ensure that you have virtualization enabled in BIOS (Google it for your machine's model).
* Tested on: Windows 7, 8, and 10.

### Mac

* Tested with VirtualBox 5.2.10: https://download.virtualbox.org/virtualbox/5.2.10/VirtualBox-5.2.10-122088-OSX.dmg
* Tested with Vagrant 2.1.1: https://releases.hashicorp.com/vagrant/2.1.1/vagrant_2.1.1_x86_64.dmg
* Git is required: http://git-scm.com/downloads
* Tested on: OS/X Yosemite, and El Capitan, and Sierra.

### Linux

* VirtualBox 5.2.10 can be downloaded here: https://www.virtualbox.org/wiki/Linux_Downloads
* Vagrant 2.1.1 can be downloaded here: https://releases.hashicorp.com/vagrant/2.1.1/
* On newer machines, ensure that you have virtualization enabled in BIOS (duckduckgo it for your machine's model).

**Fedora 25, CentOS 7**

These are available via the package manager.

```
$ sudo dnf install vagrant
$ sudo dnf install VirtualBox
```

## Get Started

* Create and add a public SSH key to your git server (GitHub, GitLab, etc).
* Clone the repository and bring up the virtual development environment. The first time you install the box, "vagrant up" will take a little while. Grab a cup of coffee or something!
* The Vagrant plugin `vagrant-vbguest` will cause problems with the shared folder in most cases. Please uninstall the plugin first if you have it installed with `vagrant plugin uninstall vagrant-vbguest`.

```bash
git clone --recursive https://github.com/Pleiades-Spiri/spiri-ansible-vagrant.git
cd spiri-ansible-vagrant
vagrant up
vagrant ssh
```

* You can also add the host name to your computer's `hosts` file. Your `hosts` file should be located at:

    * Mac / Linux: /etc/hosts
    * Windows: %SystemRoot%\system32\drivers\etc\hosts

Add this line (with the appropriate host name, if you changed it):

```
192.168.99.99  vagrant.spiri.com
```

### Default installation creates

    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key

```
$ vagrant ssh
```

Another, less desirable, option for SSH'ing into the vagrant box..
(this requires the use of the default password, vagrant)

```
$ ssh vagrant@vagrant.my.domain.com -p 2222
```

At this point, you should change the default password for the vagrant user.
You may also want to add/remove users soon.

Maintainer:

* Tim Allen (https://github.com/FlipperPA)
