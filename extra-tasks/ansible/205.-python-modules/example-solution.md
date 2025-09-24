# Example solution

### Python module

{% code title="check_restconf_status.py" %}
```yaml
# Written by Andreas Koksrud, based on framework from Erik Rongved and Espen Frøstrup.
from ansible.module_utils.basic import AnsibleModule

def run_module():
    # Define available arguments/parameters available to pass to the module from Ansible
    module_args = dict(
        hostname=dict(type='str', required=True),
        show_run=dict(type='str', required=True),
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

    # We start populating the result object with the hostname of the WLC.
    result['hostname']=module.params['hostname']

    # Then we check if the text "restconf" is present in the run-config, and write some 
    # corresponding values to the result object to pass back to Ansible
    if "restconf" in module.params['show_run']:
        result['restconf_enabled']=True
        result['comments']="RESTCONF status: Enabled"
    else:
        result['restconf_enabled']=False
        result['comments']="RESTCONF status: Disabled"

    # After doing the work, return the result back to Ansible as JSON
    module.exit_json(**result)


def main():
    run_module()

if __name__ == '__main__':
    main()

```
{% endcode %}

### Ansible playbook

{% code title="module-playbook.py" %}
```yaml
---

- name: Module demo
  hosts: wlc
  connection: network_cli
  gather_facts: false

  tasks:

    - name: Gather IOS facts
      cisco.ios.ios_facts:
        gather_subset: all
      register: facts

    - name: Check if RESTCONF is enabled
      check_restconf_status:
        hostname: "{{ facts.ansible_facts.ansible_net_hostname }}"
        show_run: "{{ facts.ansible_facts.ansible_net_config }}"
      register: result

    - name: Write results to YAML file
      ansible.builtin.copy:
        dest: "./logs/audit_{{ facts.ansible_facts.ansible_net_hostname }} ({{ '%Y-%m-%d' | strftime }}).yml"
        mode: "0600"
        content: "{{ result | to_nice_yaml }}"

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

### Example output

<figure><img src="../../../.gitbook/assets/image (200).png" alt=""><figcaption></figcaption></figure>

### Example of the logfile written (as YAML)

<figure><img src="../../../.gitbook/assets/image (201).png" alt="" width="397"><figcaption></figcaption></figure>

### Example of the logfile written (as JSON)

<figure><img src="../../../.gitbook/assets/image (202).png" alt="" width="467"><figcaption></figcaption></figure>

