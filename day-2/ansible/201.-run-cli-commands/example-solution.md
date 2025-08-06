# Example solution

Here is an example solution:

{% code title="run-cli-command-playbook.yml" %}
```yaml
---
- name: CLI Playbook
  hosts: wlc
  connection: network_cli
  gather_facts: false

  tasks:

    - name: "Get Max APs supported with CLI command"
      cisco.ios.ios_command:
        commands: "show wireless summary | include Max APs"
      register: result

    - name: "View result"
      ansible.builtin.debug:
        msg: "{{ result.stdout }}"

```
{% endcode %}

The output should look similar to this:

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure></div>
