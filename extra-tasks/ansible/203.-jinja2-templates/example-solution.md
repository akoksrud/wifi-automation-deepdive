# Example solution

Here is an example solution:

{% code title="jinja2-playbook.yml" %}
```yaml
---
- name: CLI configuration using Jinja2 template
  hosts: wlc
  connection: network_cli
  gather_facts: false

  tasks:

    - name: "Configure policy profile from template: {{ item.name }}"
      cisco.ios.ios_config:
        before:
          - wireless profile policy {{ item['name'] }}
          - shutdown 
        src: policy_profile_template.j2
        match: line
        after:
          - no shutdown
      loop: "{{ policy_profiles }}"

```
{% endcode %}

{% code title="policy_profile_template.j2" %}
```yaml
wireless profile policy {{ item['name'] }}
 session-timeout 43200
 vlan {{ item['vlan'] }}
 no shutdown
```
{% endcode %}

{% code title="hosts.yml" %}
```yaml
wlc:
  hosts:
    192.168.10.{WLC-IP}:
  vars:
    ansible_connection: network_cli
    ansible_network_os: ios
    ansible_ssh_pass: ChangeMe2025!
    ansible_password: ChangeMe2025!
    ansible_user: devnet-adm
    ansible_host_key_checking: False
    policy_profiles:
      - name: policy_profile_j2
        vlan: 11
      - name: policy_profile_j2_2
        vlan: 12
      - name: policy_profile_j2_3
        vlan: 13

```
{% endcode %}

* Change <kbd>{WLC-IP}</kbd> with your WLC IP (192.168.10.51, 52, 53, 54, 55, 56, etc)

### Further exploration / tasks

Can you change more parameters (ex. session-timeout value)?

Can you create templates for other stuff? Loopback interfaces (safe to play with), wlans, site tags, etc?

