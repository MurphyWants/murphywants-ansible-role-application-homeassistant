# ansible-role-template

Purpose:

```
Image: ''
tag: latest # unless otherwise specificed in the variables
```

This role will:

## Requirements/Dependencies
Uses the following modules:

Uses the following roles:

## Tags
Ansible role template with the following actions & tags:

Tag | Description
--- | ---
Setup/Baseline | Setup the application and apply the configuration baseline
Start | Start required services
Stop | Stop required services
Backup | Run the backup for the component or application or OS
Update | Update the component applications
Remove | Remove configurations and applications
Purge | Remove all configurations and applications relating to the app/component

## Variables
Variable | Default Value | Description
---|---|---

## Example Playbook

playbook.yml
```
- hosts: all 
  gather_facts: yes
  become: yes
  roles:
  - role: ansible-role
```

## Example Inventory

static.ini
```
[all]
hostname

[all:vars]
var=var
```

# TODO List
