# The Ansible Controller
The setup files for the controller, web, and database vms were provided for us.  

### The Hosts File
This is the inventory. Information about the agents goes here.

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
