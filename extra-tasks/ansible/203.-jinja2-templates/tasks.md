# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>ansible-j2-templates</kbd>
* Create a playbook file <kbd>jinja2-playbook.yml</kbd>&#x20;
* Create a template file <kbd>policy\_profile\_template.j2</kbd>&#x20;
* Copy the <kbd>hosts.yml</kbd> file from the previous tasks

<figure><img src="../../../.gitbook/assets/image.png" alt="" width="281"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1).png" alt=""><figcaption></figcaption></figure></div>



### Task 1: Write a playbook using a Jinja2 template

* Ensure that this policy profile is present on the WLC

<figure><img src="../../../.gitbook/assets/image (1).png" alt="" width="483"><figcaption></figcaption></figure>

* Verify the idempotency (changes stuff only when needed)

### Task 2: Change some of the text in the j2 template

* Use a variable for the name and the VLAN ID
* Use a loop statement in the task to do multiple policy profiles with the same template
* You can copy the inventory file hosts.yml from Day 1
* Change <kbd>{WLC-IP}</kbd> with your WLC IP (192.168.10.51, 52, 53, 54, 55, 56, etc)

{% code title="hosts.yml" %}
```yaml
wlc:
  hosts:
    192.168.10.{WLC-IP}:
  vars:
    ansible_connection: network_cli
    ansible_network_os: ios
    ansible_ssh_pass: restconf-pass
    ansible_password: restconf-pass
    ansible_user: restconf-adm
    ansible_host_key_checking: False

```
{% endcode %}
