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

In the task, if you try to change the VLAN ID from 11 to 12, you will notice that nothing changes on the WLC. That is because the policy profile needs to be shutdown before making changes if it already exists. You can test this on your WLC with the following commands:

```
wlc9# wlc9#conf t
wlc9(config)# wireless profile policy clients_policy_profile
wlc9(config-wireless-policy)# vlan 12
% Policy profile needs to be disabled before performing this operation.
```

To address this, we can use the <mark style="color:orange;">before:</mark> and <mark style="color:orange;">after:</mark> statements in the task, to get Ansible to add certain commands before and after the lines that we compare. The before and after sections will only be run if the task itself would create a change (i.e. if the lines do not match)

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>(part of) cli-config-playbook.yml</p></figcaption></figure>

1. These lines will be entered before the lines that we compare
2. Since we enter "no shutdown" after the lines themselves, we do not need this in the lines
3. These lines will be entered after the lines that we compare
