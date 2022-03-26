# Hello World example
## Explanation 

This is an example of an playbook that runs a series of tasks against localhost. 

You can simply run tasks from a playbook. 

How playbooks work: https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html

## Run 
Run the command like: 

```
ansible-playbook hello-world.yaml
```


## Output 
It'll then have output like this: 

```
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

PLAY [Hello World example] *************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [localhost]

TASK [Set a variable to "foo"] *********************************************************************************************************
ok: [localhost]

TASK [Echo the variable] ***************************************************************************************************************
ok: [localhost] => {
    "some_variable": "foo"
}

TASK [Run a command, register it] ******************************************************************************************************
changed: [localhost]

TASK [Output the cmd_result] ***********************************************************************************************************
ok: [localhost] => {
    "cmd_result": {
        "changed": true,
        "cmd": [
            "ip",
            "link"
        ],
        "delta": "0:00:00.001926",
        "end": "2022-03-26 13:35:11.710940",
        "failed": false,
        "rc": 0,
        "start": "2022-03-26 13:35:11.709014",
        "stderr": "",
        "stderr_lines": [],
        "stdout": "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000\n,
        "stdout_lines": [
            "1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000",
            "    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00",
        ]
    }
}

PLAY RECAP *****************************************************************************************************************************
localhost                  : ok=5    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   