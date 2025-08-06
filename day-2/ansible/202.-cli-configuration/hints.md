# Hints

The structure of the file should be like this:

<figure><img src="../../../.gitbook/assets/image (178).png" alt=""><figcaption><p>cli-config-playbook.yml</p></figcaption></figure>

1. Instead of this placeholder, you would use a module that can do CLI config on Cisco IOS devices. Try looking in the cisco.ios collection in the Ansible Docs\
   [https://](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[docs.ansible.com](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[/ansible/latest/collections/cisco/](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[ios](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[/](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)[index.html#plugins-in-cisco-ios](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html)
2. The module needs all the config lines that we want, as an ordered list, after a parameter specifying all those lines
3. The module also needs a parameter specifying which parent the config lines should belong to. The parent in this example is the policy profile. In another example it might be an interface, a WLAN, a site tag etc.



Run the playbook with this command:

```bash
ansible-playbook -i hosts.yml cli-config-playbook.yml
```



### Expanding the playbook









