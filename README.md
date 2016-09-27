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

### Example output

```

PLAY [test] ********************************************************************

TASK [setup] *******************************************************************
ok: [dhcp31-3.perf.lab.eng.bos.redhat.com]

TASK [Install sos via dnf] *****************************************************
ok: [dhcp31-3.perf.lab.eng.bos.redhat.com] => (item=[u'sos', u'rsync', u'ansible'])

TASK [Install sos via yum] *****************************************************
skipping: [dhcp31-3.perf.lab.eng.bos.redhat.com] => (item=[]) 

TASK [Install rsync on local] **************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com -> localhost]

TASK [results directory] *******************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com -> localhost]

TASK [c] ***********************************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com]

TASK [sync] ********************************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com -> localhost]

TASK [see that dir is empty] ***************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com]

TASK [Run sosreport] ***********************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com]

TASK [Sync the results from remote] ********************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com]

TASK [Delete the results] ******************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com]

TASK [Create dir for ansible_facts] ********************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com -> localhost]

TASK [Collect ansible_facts] ***************************************************
changed: [dhcp31-3.perf.lab.eng.bos.redhat.com -> localhost]

PLAY RECAP *********************************************************************
dhcp31-3.perf.lab.eng.bos.redhat.com : ok=12   changed=10   unreachable=0    failed=0

```
