# Digital_Forensic_Tools_for_AWS_EC2
The code to provision an EC2 instance and install basic Digital Forensic tools.

## Prerequisites ##

Create and download IAM access keys for the root of your AWS account

Create and download a key pair for SSH connection

Create an Ansible vault with the following command
```
ansible-vault create group_vars/all/pass.yml 
```
The format of the keys should be as follows: 
```
ec2_access_key: AAAAAAAAAAAAAABBBBBBBBBBBB                                       
ec2_secret_key: afjdfadgf$fgajk5ragesfjgjsfdbtirhf 
```
## Provision Instance 
Provision instances with the following command:
```
ansible-playbook EC2.yml --ask-vault-pass 
```

Add the public DNS address of the newly created EC2 to the host file
```
/etc/ansible/hosts
```
## Install Tools 
Install tools on the machine by using the following command (change keyname.pem to your SSH key):
```
ansible-playbook --private-key=./keyname.pem Modules.yml --ask-vault-pass
```

## SSH into EC2
Change keyname.pem to your SSH key and the address to your instance public DNS address.
```
ssh -i "keyname.pem" admin@ec2address.region.amazonaws.com 
```
