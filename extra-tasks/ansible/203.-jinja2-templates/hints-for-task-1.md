# Hints for Task 1

The structure of the file should be like this:

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

1. This is where we put in the Jinja2 template file we created
2. Now, go ahead and fill inn the "policy\_profile\_template.j2" file:

```
wireless profile policy clients_policy_profile_j2
 session-timeout 43200
 vlan 11
 no shutdown
```

Run the playbook with this command:

```bash
ansible-playbook -i hosts.yml jinja2-playbook.yml
```
