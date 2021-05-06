# The Ansible Controller
Setup of controller and web and database instances

## Controller Setup
Create an EC2 instance and SSH into it. For the perposes of this, make sure you can do that from your local machine.

Inside the machine, create `provsion.sh` with the following commands:
```
#!/bin/bash
# run this file in the controller

sudo apt-get update -y
sudo apt-get install software-properties-common -y
sudo apt-add-repository ppa:ansible/ansible -y
sudo apt-get update -y
sudo apt-get install ansible -y

sudo apt-get install tree

# dependancies for vault
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y
sudo apt install python3-pip -y

sudo apt-get update -y
sudo apt-get upgrade -y

pip3 install awscli
pip3 install boto boto3
```

Make it executable then run it.

## Creating Instances
Setup playbook (look to file) and make minor edits so that it creates **two** instances. One for web and another for the database.  

Setup vault file. First setup the required file structure.
```
sudo mkdir group_vars
cd group_vars
sudo mkdir all
```
Now you can run:
```
sudo ansible-vault create pass.yml
```

In that file do:
```yml
aws_access_key: THISISMYACCESSKEY
aws_secret_key: THISISMYSECRETKEY

```
This opens a file in vim. You'll need to hit `i` before you can edit the file and `ESC` to stop editing.
After hitting `ESC` do `:wq` and enter to save and quit.

Now run
```
sudo ansible-playbook instance_setup.yml --ask-vault-pass -t create_ec2
```

<!--
All of this is just to keep track of how badly I messed up, lol

# to keep track so I can make clean notes later

Link to provision setup: https://medium.datadriveninvestor.com/devops-using-ansible-to-provision-aws-ec2-instances-3d70a1cb155f

After setting up ec2 instance, ran the following: 
```
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt-get install ansible -y
sudo apt-get install python3-pip -y
pip3 install awscli
pip3 install boto boto3
```

Then moved on to generating key, using
```
ssh-keygen -t rsa -b 4096 -f ~/.ssh/my_aws
```
`my_aws` is just the key name

Remembered to install tree now...
```
sudo apt-get install tree
```

Following guide, created the directory structure I needed
```
mkdir -p AWS_Ansible/group_vars/all/
cd AWS_Ansible
touch playbook.yml
```

Now to securely store the aws keys
```
ansible-vault create group_vars/all/pass.yml
```
This creates a file and opens it in vi/vim. Use `i` to start entering values and `ESC` when you're done. To save and quit do `:wq`. The order is important.  

Noting down this image: ami-0943382e114f188e8

Remembered to drop this into the sshd_config file to make sure the correct version of python is running
```
[local]
localhost ansible_python_interpreter=/usr/bin/python3
```

Having trouble and getting this error
```
fatal: [localhost]: FAILED! => {"changed": false, "msg": "boto3 required for this module"}
```

Ran these to see if it would change anything
```
sudo apt-get install python -y # wasn't needed
sudo apt-get install python-pip -y
pip install boto boto3 ansible
```

It seems like I need to uninstall then reinstall ansible... -->