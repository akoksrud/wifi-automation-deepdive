# 208. Roles

Instead of using a master playbook to run other playbooks, in this exercise we will use "roles" to call tasks on each device that has that role

The example will still be somewhat constructed and simplified to primarily show the concept of roles rather than being super-useful in the real world by itself

This example contains two roles:

* `get_version`: This role gets and prints the current version of the device, and is applied to all our devices (reuse some of the playbook from [115.-exercise-gather-facts.md](../../../main-tasks/ansible/115.-exercise-gather-facts.md "mention"))
* `get_max_aps`: This gets the maximum number of APs on a WLC, it is applied only to the WLC (reuse playbook from [201.-run-cli-commands](../201.-run-cli-commands/ "mention"))

Reference: [https://docs.ansible.com/ansible/latest/network/getting\_started/network\_roles.html](https://docs.ansible.com/ansible/latest/network/getting_started/network_roles.html)
