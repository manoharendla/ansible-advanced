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