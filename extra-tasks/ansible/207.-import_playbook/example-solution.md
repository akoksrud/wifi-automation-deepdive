# Example solution

### Main playbook

{% code title="audit-network-playbook.yml" %}
```yaml
---
- name: Audit WLCs
  ansible.builtin.import_playbook: audit_playbooks/audit-wlcs-playbook.yml
- name: Audit switches
  ansible.builtin.import_playbook: audit_playbooks/audit-switches-playbook.yml
- name: Audit routers
  ansible.builtin.import_playbook: audit_playbooks/audit-routers-playbook.yml

```
{% endcode %}



### Sub playbooks

{% code title="audit-routers-playbook.yml" %}
```yaml
---
- name: Audit routers
  hosts: router
  connection: network_cli
  gather_facts: false
  tasks:
    - name: Gather IOS facts
      cisco.ios.ios_facts:
        gather_subset: all
      register: facts1
    - name: Output hostname and version
      ansible.builtin.debug:
        msg: "Hostname: {{ facts1.ansible_facts.ansible_net_hostname }} (version {{ facts1.ansible_facts.ansible_net_version }})"

```
{% endcode %}

{% code title="audit-switches-playbook.yml" %}
```yaml
---
- name: Audit switches
  hosts: switch
  connection: network_cli
  gather_facts: false
  tasks:
    - name: Gather IOS facts
      cisco.ios.ios_facts:
        gather_subset: all
      register: facts1
    - name: Output hostname and version
      ansible.builtin.debug:
        msg: "Hostname: {{ facts1.ansible_facts.ansible_net_hostname }} (version {{ facts1.ansible_facts.ansible_net_version }})"

```
{% endcode %}

{% code title="audit-wlcs-playbook.yml" %}
```yaml
---
- name: Audit WLCs
  hosts: wlc
  connection: network_cli
  gather_facts: false
  tasks:
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

<figure><img src="../../../.gitbook/assets/image (208).png" alt=""><figcaption></figcaption></figure>

Since we do not have a "router" group in our hosts.yml file, we get a warning when we run the playbook since it does not match any host groups:\
<mark style="color:purple;">\[WARNING]: Could not match supplied host pattern, ignoring: router</mark>
