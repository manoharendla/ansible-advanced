# ansible-advanced


## Notes

## Ansible Vault commands

### Create a vault-id password file
echo "Some encrypted vault id" > vault-id-password-file

### Encrypt a string
* ansible-vault encrypt_string "string_name" -n "key_name" --vault-id vault-id-password-file
`code
[osboxes@ansible-controller ~]$ ansible-vault encrypt_string "one" -n two > 1.yml --vault-id v
[osboxes@ansible-controller ~]$ cat 1.yml
two: !vault |
          $ANSIBLE_VAULT;1.1;AES256
          64326563333765396538333738363266656632613864623830393034643731346230316439643833
          6565666666336561653064323938386237343631303361360a363461363732383162623834363861
          36653465396266616233353336666239623931663561356533316466636462613664343265383638
          6635643933333161340a626430353039353238313766313231653565356561666435393665653366
         3830`

### Decrypt a string 
* ansible localhost -m debug -a var='two' -e "@1.yml" --vault-id v
`code
localhost | SUCCESS => {
    "two": "one"
}
`

## Ping pong for 4 servers
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


## Ansible tower

### Logon to ansible tower with admin/admin
![](images/login.png)

### Create Credentials for gihtub token. The credentials involved in Ansible tower and github communication
![](images/cred1.png)

![](images/cred2.png)

### Create Credentials for SSH login. The credentials involved in Ansible tower and target servers communication
![](images/ssh-creds.png)

### Creating a project
![](images/createproject.png)

### Creating an inventory
![](images/inv1.png)

### Creating an inventory source to find the inventory yaml
![](images/inv2.png)

### Run sync to fetch the host and groups from inventory yaml
![](images/invsync.png)
![](images/listofhosts_added.png)

### Create a job template
![](images/job_template.png)

### Scheduling and Notifications Options
![](images/Schedule_OR_Notification.png)

### Launch job
![](images/launch_job.png)

