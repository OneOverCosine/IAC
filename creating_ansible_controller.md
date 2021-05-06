# This is more of an informational file - I would go elsewhere for setup instructions


## The Ansible Controller
The setup files for the controller, web, and database vms were provided for us.  

### The Hosts File
This is the inventory. Information about the agents goes here.

### Playbooks
These are files with the extention .yml/.yaml. They contain a set of instructions (or tasks) to do the configuration management.  

We'll be creating the playbook(s) in the `/etc/ansible` directory.  

While writing these files, be aware of indentation. Do *not* use tabs. Instead use spaces to get the desired indentation.  

This first playbook is used to install Nginx for the web agent. The commented code restarts service. It's out of date or incorrect, so it's not being used.
```yml
# This is an example of an ansible playbook written in YAML
# A YAML file begins with three dashes (---)
---

# hosts is to define the name of your host machine. You could also use 'all' to run the task for all servers
- hosts: web

  # gather facts before performing any tasks
  gather_facts: yes

  # to run in admin mode
  become: true

  # every task should have a name which is included in the output
  # the goal of each task is to execute a module with very specific arguments

  # In this tasks we need to install Nginx on the web server
  tasks:

  - name: Installing Nginx
    apt: pkg=nginx state=present
    #notify:
    #- restart nginx
    #- name: Enable nginx during boot
    #  service: name=nginx state=started enabled=yes
```

To run a playbook:
```
ansible-playbook [playbook_name]
```

## Useful Commands
Remember to check the [documentation](https://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html) for more info.

`ping [ip]` - Allows you to check your connection to the specified ip (or website)  
`ssh vagrant@[ip]` - Used to ssh into the VM with the specified ip  

### Using Ad-hoc commands
To run ad-hoc commands use `ansible` followed by the name of the machine, then `-a "[command]"`. It must be added to the hosts file.  
```
ansible [pattern] -m [module] -a "[module options]"
```
"pattern" is used to refer to a specific host/group which you have set up in the hosts file.

The first `-a` means adhoc
The `-m` flag means module
---
`ansible [agent_name] -m ping` - Another verion of the ping command. Let's you ping a named agent.  
`ansible all -m shell -a "uptime"` - Used to the uptime for all machines in your host file.  
`--become` - Appened to the end of a command, this allows you to run it in admin mode.  
`ansible-playbook rds_prod.yml  --syntax-check` - useful for cheking syntax

https://docs.ansible.com/ansible/latest/collections/amazon/aws/ec2_module.html

