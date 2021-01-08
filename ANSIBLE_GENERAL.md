### Ping pong for 4 servers
`code
[root@ansible-controller webapp]# ansible all -m ping -i inventory.yml
target2 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
target5 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
target6 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
target1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
`

### Validation mode
`code [root@ansible-controller webapp]# ansible-playbook webapp.yml -i inventory.yml --check`

### Create a role skelton using ansible-galaxy
`code [root@ansible-controller role-mano]# ansible-galaxy role init <name>`

