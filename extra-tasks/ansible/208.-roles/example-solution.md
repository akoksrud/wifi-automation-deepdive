# Example solution

### Main playbook

{% code title="audit-network-playbook.yml" %}
```yaml
---
- name: Get version from all Cisco devices
  hosts: all
  connection: network_cli
  gather_facts: false
  roles:
    - get_version

- name: Get max APs
  hosts: wlc
  connection: network_cli
  gather_facts: false
  roles:
    - get_max_aps

```
{% endcode %}

### Sub playbooks

{% code title="get_max_aps/tasks/main.yml" %}
```yaml
---
- name: "Get Max APs supported with CLI command"
  cisco.ios.ios_command:
    commands: "show wireless summary | include Max APs"
  register: result

- name: "View result"
  ansible.builtin.debug:
    msg: "{{ result.stdout }}"

```
{% endcode %}

{% code title="get_version/tasks/main.yml" %}
```yaml
---
- name: Gather IOS facts
  cisco.ios.ios_facts:
    gather_subset: all
  register: facts1

- name: Output hostname and version
  ansible.builtin.debug:
    msg: "Hostname: {{ facts1.ansible_facts.ansible_net_hostname }} (version {{ facts1.ansible_facts.ansible_net_version }})"

```
{% endcode %}

### Hosts file

{% code title="hosts.yml" %}
```yaml
all:
  children:
    wlc:
      hosts:
        192.168.10.9:
        192.168.10.30:
    switch:
      hosts:
        192.168.10.2:
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

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>
