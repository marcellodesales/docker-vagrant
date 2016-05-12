# docker-vagrant


## What's This About?
The purpose of this project is to easily fire up a VMs with a running Docker.

## Preparation of *Ubuntu* Host

### `virtualbox`
```bash
sudo apt-get install virtualbox
```

### *Vagrant* 1.8.1+
Download from [website](http://www.vagrantup.com/downloads.html), then:
```bash
sudo dpkg -i vagrant_1.8.1_x86_64.deb
```

### *Ansible* 1.9+

```
sudo apt-get remove pip
sudo apt-get install python-setuptools python-dev build-essential
sudo easy_install pip
sudo pip install ansible
```

Reboot system.

## Start instances

```
vagrant up --provider virtualbox
```

## Destroy instance

```
vagrant destroy

```

##License
Apache
