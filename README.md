# ansible_sosreport_facts
Collects sosreport, ansible_facts from remotes on to the local machine and deletes them on remotes.

## Requirements
You need to have these installed on your host
   - Ansible
   - python

### Run
$ ansible-playbook -i hosts generate.yml

### variables

SOSREPORT_PATH - Directory to save results

HOSTS_PATH - Inventory file path

### override
You can override the variables like

$ ansible-playbook --extra-vars '{"HOSTS_PATH":"/tmp/hosts"}' generate.yml
