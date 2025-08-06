# Hints

The structure of the file should be like this:

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>run-cli-command-playbook.yml</p></figcaption></figure>

1. Playbook header
   1. name: Name of the playbook, make it descriptive
   2. hosts: The "wlc" here you can find in the hosts.yml file. Can be expanded to other types.
   3. connection: network\_cli for most of our stuff
   4. gather\_facts: A general-purpose gathering function
2. Our "tasks" section starts here
3. Instead of this placeholder, you would use a module that can run CLI commands. Try looking in the <kbd>cisco.ios</kbd> collection in the Ansible Docs and look for the "ios\_command" module.\
   [https://](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[docs.ansible.com](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[/ansible/latest/collections/cisco/](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[ios](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[/](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[index.html#plugins-in-cisco-ios](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)
4. Instead of this placeholder, you will use a module that can output stuff. The example solution uses a builtin module to output the text in "results" as a debug message when you run the playbook. Try looking for "debug" in the ansible.builtin collection\
   [https://](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)[docs.ansible.com](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)[/ansible/latest/collections/ansible/](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)[builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)[/](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)[index.html#plugins-in-ansible-builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)

Run the playbook with this command:

```bash
ansible-playbook -i hosts.yml run-cli-command-playbook.yml
```
