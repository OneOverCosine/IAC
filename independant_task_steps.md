# to keep track so I can make clean notes later

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

Remembered to drop this into the sshd_config file to make sure the correct version of python is running
```
[local]
localhost ansible_python_interpreter=/usr/bin/python3
```
