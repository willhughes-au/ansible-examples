# Playbook with Inventory

Inventory files allow you specified groups of hosts to run tasks against. 

How inventory works: https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html#inventory-basics-formats-hosts-and-groups

You can use the default inventory file on your machine, or pass one in using the `-i` argument to ansible-playbook. 

Within the playbook you can target groups or individual hosts.

## Run

```
ansible-playbook -i my-inventory-file some-playbook.yaml
```


## Output

```
PLAY [Run on all servers] **************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [gpuhost01]
ok: [sensepi01]
ok: [nuc01]
ok: [sensepi03]
ok: [sensepi02]

TASK [Run a command, register it] ******************************************************************************************************
changed: [gpuhost01]
changed: [nuc01]
changed: [sensepi01]
changed: [sensepi03]
changed: [sensepi02]

TASK [Output the cmd_result] ***********************************************************************************************************
ok: [gpuhost01] => {
    "cmd_result.stdout": "gpuhost01"
}
ok: [nuc01] => {
    "cmd_result.stdout": "nuc01"
}
ok: [sensepi01] => {
    "cmd_result.stdout": "sensepi01"
}
ok: [sensepi02] => {
    "cmd_result.stdout": "sensepi02"
}
ok: [sensepi03] => {
    "cmd_result.stdout": "sensepi03"
}

TASK [Output datacenter] ***************************************************************************************************************
ok: [nuc01] => {
    "datacenter": "VARIABLE IS NOT DEFINED!"
}
ok: [gpuhost01] => {
    "datacenter": "VARIABLE IS NOT DEFINED!"
}
ok: [sensepi01] => {
    "datacenter": "distributed"
}
ok: [sensepi02] => {
    "datacenter": "distributed"
}
ok: [sensepi03] => {
    "datacenter": "distributed"
}

PLAY [Run on just pi group] ************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [sensepi01]
ok: [sensepi03]
ok: [sensepi02]

TASK [Run a command, register it] ******************************************************************************************************
changed: [sensepi01]
changed: [sensepi03]
changed: [sensepi02]

TASK [Output the cmd_result] ***********************************************************************************************************
ok: [sensepi01] => {
    "cmd_result.stdout": "sensepi01"
}
ok: [sensepi02] => {
    "cmd_result.stdout": "sensepi02"
}
ok: [sensepi03] => {
    "cmd_result.stdout": "sensepi03"
}

PLAY RECAP *****************************************************************************************************************************
gpuhost01                  : ok=4    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
nuc01                      : ok=4    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
sensepi01                  : ok=7    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
sensepi02                  : ok=7    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
sensepi03                  : ok=7    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```
