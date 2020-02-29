## Install Python3 and VirtualEnv (for Mac)

1. Open a terminal 

2. Run the following commands

```
brew update
brew install python
python3 --version
pip3 install virtualenv 
mkdir ansible101
cd ansible101
virtualenv ansible101
source ansible101/bin/activate
pip install ansible
```
Your prompt should look something like this when the above steps are completed:

```
(ansible101) [lckam:diva - ansible101]->
```

## Configure Inventory Hosts File
echo "[group1]
host1 ansible_host=68.183.96.251 ansible_ssh_port=22
[group2]
host2 ansible_host=167.99.236.136 ansible_ssh_port=22" > inventory_hosts

## Install sshpass (needed for using ssh username and password)
```
brew install https://raw.githubusercontent.com/kadwanev/bigboybrew/master/Library/Formula/sshpass.rb
```


## Ansible Ad-Hoc commands go here

This command will attempt to connect to the servers in the inventory file to validate that Ansible can connect

```
ansible -i inventory_hosts  all -m ping --extra-vars "ansible_user=root ansible_password=hwthdc2020"
```

## Ansible Playbook with one Play, but multiple tasks

Run the command below to create a playbook

**We are using a shared set of servers.  So, feel free to install something other this nginx.  Only one person will be able to install nginx**

```
echo "---
- hosts: all
  tasks:
    - name: ensure nginx is at the latest version
      apt: name=nginx state=latest
    - name: start nginx
      service:
          name: nginx
          state: started" > play1.yml
```

Dry-Run the play

```
ansible-playbook  -i  inventory_hosts play1.yml --check --extra-vars "ansible_user=root ansible_password=hwthdc2020"
```

Execute the play

**We are using a shared set of servers.  So, feel free to install something other this nginx.  Only one person will be able to install nginx**

```
ansible-playbook  -i  inventory_hosts play1.yml --extra-vars "ansible_user=root ansible_password=hwthdc2020"
```


## Clean Up Your Environment
```
# deactivate virtual environment 
deactivate
 
#To remove the virtual environment:   
rm -rf ansible101
