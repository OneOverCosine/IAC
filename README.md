# Infrastructure As Code

## What is IAC?
It's a method of provisioning and managing IT infrastructure through machine readable definition files. This is instead of using opperating procedures and manual processes.

## Types of IAC
- Mutable or immutable
- On premises or cloud 

## Benefits of Using IAC
+ Speed and simplicity
+ Configurating consistency
+ Less risk
+ More efficient
+ Saves costs

## Best Practice
- Codify everything
- Document as little as possible
- Maintain version control
- Continuously test, intergrate, and deploy

## Two IAC Types
**Config management** - For provisioning and maintaining the state of systems.  
**Orchestration** - After creating templates for all parts of the system, we need orchestration tools and scripts that talk to the cloud and pull them together into the architechture.

## What is Ansible?

## What is Ansible Vault?
There are many ways to keep our AWS keys secure. When using Ansible, we can use Ansible Vault to keep our keys secure.  
Other methods:  
- Use .gitignore
- SSH to access machines
- Use env variables
<!-- - (SSH agent) -->

Using Ansible Vault is more secure.  
Vault uses boto3

## [Setting Up Ansible Controller](independant_task_steps.md)
Among other things...