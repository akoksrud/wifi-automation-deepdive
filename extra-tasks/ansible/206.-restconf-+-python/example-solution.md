# Example solution

### Playbook

{% code title="interface-playbook.yml" %}
```yaml
---

- name: Interface Playbook
  hosts: wlc
  connection: network_cli
  gather_facts: false

  tasks:

    - name: Get Interface list with RESTCONF
      ansible.builtin.uri:
        url: "https://{{ ansible_host }}/restconf/data/Cisco-IOS-XE-native:native/interface?fields=GigabitEthernet/name;GigabitEthernet/description"
        user: "{{ ansible_user }}"
        password: "{{ ansible_password }}"
        method: GET
        headers:
          Content-Type: 'application/yang-data+json'
          Accept: 'application/yang-data+json'
        body_format: json
        body:
        validate_certs: false
        status_code:
          - 200
          - 204
          - 404
      register: restconf_result

    - name: Do something with the interface list in a Python module
      update_description:
        interface_dict: "{{ restconf_result['json'] }}"
      register: update_description_result
      when: restconf_result.status == 200

    - name: View result
      ansible.builtin.debug:
        msg: "{{ update_description_result }}"
      when: restconf_result.status == 200

    - name: Update Interface list with RESTCONF
      ansible.builtin.uri:
        url: "https://{{ ansible_host }}/restconf/data/Cisco-IOS-XE-native:native/interface"
        user: "{{ ansible_user }}"
        password: "{{ ansible_password }}"
        method: PATCH
        headers:
          Content-Type: 'application/yang-data+json'
        body_format: json
        body: "{{ update_description_result.new_interface_dict }}"
        validate_certs: false
        status_code:
          - 200
          - 204
          - 404
      register: restconf_write_result

    - name: View result from RESTCONF write
      ansible.builtin.debug:
        msg: "{{ restconf_write_result }}"
      when: restconf_write_result.status == 204



```
{% endcode %}

### Python module

{% code title="library/update_description.py" %}
```python
# Written by Andreas Koksrud, based on framework from Erik Rongved and Espen Frøstrup.
from ansible.module_utils.basic import AnsibleModule
from datetime import datetime

def run_module():
    # Define available arguments/parameters available to pass to the module from Ansible
    module_args = dict(
        interface_dict=dict(type='dict', required=True),
    )

    # Define the result object (which is passed back to Ansible)
    result = dict(
        changed=False
    )

    # Define the AnsibleModule object that will be instatiated when the module runs
    module = AnsibleModule(
        argument_spec=module_args,
        supports_check_mode=True
    )

    # From this point and down, is where the actual "doing" of the module takes place

    interface_dict = module.params['interface_dict']
    timestamp = datetime.now().strftime('%D %H:%M:%S')
    description = interface_dict['Cisco-IOS-XE-native:interface']['GigabitEthernet'][0]['description']

    # If the description field contains "Uplink" we will do nothing. If not, we will change the description including a timestamp just for fun
    if "Uplink" in description:
        result['Gi1_old_description'] = description
        result['Gi1_new_description'] = description
        result['new_interface_dict'] = interface_dict
        result['comments'] = f"Unchanged"
    else:
        result['Gi1_old_description'] = description
        result['Gi1_new_description'] = f"Uplink - modified {timestamp}"
        interface_dict['Cisco-IOS-XE-native:interface']['GigabitEthernet'][0]['description'] = f"Uplink - modified {timestamp}"
        result['new_interface_dict'] = interface_dict
        result['changed'] = True
        result['comments'] = f"Changed {timestamp}"

    # After doing the work, return the result back to Ansible as JSON
    module.exit_json(**result)


def main():
    run_module()

if __name__ == '__main__':
    main()
```
{% endcode %}

### Hosts file

{% code title="hosts.yml" %}
```yaml
wlc:
  hosts:
    192.168.10.9:
    192.168.10.30:
  vars:
    ansible_connection: network_cli
    ansible_network_os: ios
    ansible_ssh_pass: ChangeMe2025!
    ansible_password: ChangeMe2025!
    ansible_user: devnet-adm
    ansible_host_key_checking: False

```
{% endcode %}

### WLC config before and after changes

Before:\
![](<../../../.gitbook/assets/image (28).png>)

After:\
![](<../../../.gitbook/assets/image (29).png>)

### Example output

Some comments

* <mark style="color:red;">`fatal`</mark><mark style="color:red;">:</mark> One of the WLCs were not available when the example was run. That is the red text on the "fatal:" line
* <mark style="color:yellow;">`changed`</mark><mark style="color:yellow;">:</mark> The Python module did something to the input. Since we put result\['changed']=True, it will report that the task did change something
* `TASK [View result]`: View result from the Python module, here we can see the full "result", including the new interface dict which we use in the RESTCONF task to write to the WLC next
* `TASK [Update Interface list with RESTCONF]`: Here we have written to WLC using RESTCONF
* `TASK [View result from RESTCONF write]`: Print the write result

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure></div>

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure></div>
