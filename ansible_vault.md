# Ansible Vault

Inside the controller VM/instance
```
sudo apt-add-repository --yes --update ppa:ansible/ansible
```

Vault runs using boto3, so we need to install python
```
sudo apt-get install python3-pip -y
```

Update and upgrade
```
sudo apt-get update -y
sudo apt-get upgrade -y
```

Now to install awscli and boto3
```
pip3 install awscli
pip3 install boto boto3
```

Nagivate to `/etc/ansible/` then create two new directories: `group_vars` then inside of that `all`.
```
sudo mkdir group_vars
cd group_vars
sudo mkdir all
```

Create a file for the access and secret keys.
```
sudo ansible-vault create pass.yml
```

This opens a file in vim/vi. You'll need to hit `i` before you can edit the file and `ESC` to stop editing.
```yml
aws_access_key: THISISMYACCESSKEY
aws_secret_key: THISISMYSECRETKEY
```
After hitting `ESC` do `:wq` and enter to save and quit.

<!-- 
Ran these commands in this order - make note!!

sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt-get install ansible -y
sudo apt-get install python3-pip -y
pip3 install awscli
pip3 install boto boto3
-->