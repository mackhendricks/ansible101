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

## Ansible commands go here
 

 
## Clean Up Your Environment
```
# deactivate virtual environment 
deactivate
 
#To remove the virtual environment:   
rm -rf ansible101
