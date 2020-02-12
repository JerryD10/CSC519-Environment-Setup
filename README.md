# CSC519-Environment-Setup

## Before you get started

* Update opunit: `npm install opunit -g`. Ensure `opunit --version >= 0.4.4`.
* Update bakerx, take advantage of the new `--ip` option: `npm install ottomatica/bakerx -g` or `cd bakerx && npm install && npm update`. Ensure `bakerx --version` says `bakerx@0.6.7 virtcrud@1c9b4ba`.

## Creating your machine

Create the Virtual Machine.

```bash
bakerx run devops bionic --ip 192.168.33.10 &>/dev/null
```

Inside the machine, install nodejs and npm:

```bash
sudo curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - &>/dev/null
sudo apt-get update &>/dev/null
sudo apt-get install nodejs -y &>/dev/null
```

Next, install virtualbox:

```bash
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"
sudo apt update &>/dev/null
sudo apt install virtualbox-6.0 -y &>/dev/null
```

Now install ansible:

```bash
sudo add-apt-repository ppa:ansible/ansible -y &>/dev/null
sudo apt-get update &>/dev/null
sudo apt-get install ansible -y &>/dev/null
```

Lastly, we need bakerx and opunit to be installed:

```bash
sudo npm install opunit -g
sudo npm install ottomatica/bakerx -g
```

## Completing workshop checks

You should be able to verify all checks pass:

    opunit verify -i opunit_inventory.yml

Great work!

## Cleaning Up
Destroy your machine once done:

```bash
$ bakerx delete vm devops
```