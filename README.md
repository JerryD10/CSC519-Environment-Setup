# CSC519-Environment-Setup

## Before you get started

* Update opunit: `npm install opunit -g`. Ensure `opunit --version >= 0.4.4`.
* Update bakerx, take advantage of the new `--ip` option: `npm install ottomatica/bakerx -g` or `cd bakerx && npm install && npm update`. Ensure `bakerx --version` says `bakerx@0.6.7 virtcrud@1c9b4ba`.

## Creating your machine

Create the Virtual Machine.

```bash
bakerx run devops-machine bionic --ip 192.168.33.10
```

Inside the machine, install nodejs and npm:

```bash
sudo curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get update
sudo apt-get install nodejs -y
```

Next, install virtualbox:

```bash
sudo apt update
sudo apt upgrade
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt update
sudo apt install virtualbox-6.0 -y
```

Now install ansible:

```bash
sudo add-apt-repository ppa:ansible/ansible -y
sudo apt-get update
sudo apt-get install ansible -y
```

Lastly, we need bakerx and opunit to be installed:

```bash
sudo npm install opunit -g
sudo npm install ottomatica/bakerx -g
```

Verify installation was successful by running opunit.

```
$ opunit verify vagrant@192.168.33.10 --ssh_key ~/.bakerx/insecure_private_key -c test/devops.yml  
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