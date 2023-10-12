# murphywants-ansible-role-application-homeassistant

Purpose: Setup and configure home assistant as a docker container

```
Image: 'lscr.io/linuxserver/homeassistant'
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
HOME_ASSISTANT_PUID |  10002 | https://docs.linuxserver.io/general/understanding-puid-and-pgid
HOME_ASSISTANT_GUID |  10002 | https://docs.linuxserver.io/general/understanding-puid-and-pgid
HOME_ASSISTANT_PATH |  "/mnt/homeassistant" | The location of the container persistent data. A parition will be created and mounted here if the folder doens't exist.
HOME_ASSISTANT_STORAGE_ZFS_POOL |  'apps_pool' | The Linux host's ZFS pool name, where the partiiton will be created from
HOME_ASSISTANT_STORAGE_ZFS_FS |  'home_assistant' | The name of the filesystem that ZFS is creating
HOME_ASSISTANT_TIMEZONE |  "America/New_York" | Timezone of the container
HOME_ASSISTANT_CONTAINER_VERSION |  'latest' | Can be used to specify a specific version of the container to pull and use
HOME_ASSISTANT_DEVICE_MAPPING |  [] | An array of devices that can be passed from the host to the container. the source will be mapped to the destination

## Example Playbook

playbook.yml
```
- hosts: app_home_assistant 
  gather_facts: yes
  become: yes
  tasks:
  - name: Run the home assistant role
    ansible.builtin.import_role:
      name: murphywants-ansible-role-application-homeassistant
```

## Example Inventory

static.yml
```
all: 
  hosts:
    homeAssistantVM
app_home_assistant:
  hosts:
    homeAssistantVM
  vars:
    HOME_ASSISTANT_DEVICE_MAPPING:
      - /dev/ttyACM0
```

# TODO List
- [ ] Implment backups
- [ ] Implement all the tags
  - [ ] tag_update.yml
  - [ ] tag_remove.yml
  - [ ] tag_purge.yml
  - [ ] tag_backup.yml

