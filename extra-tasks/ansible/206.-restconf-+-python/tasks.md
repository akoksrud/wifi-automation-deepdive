# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>ansible-restconf-python</kbd>
* Create a playbook file <kbd>interface-playbook.yml</kbd>&#x20;
* Copy the <kbd>hosts.yml</kbd> file from the previous tasks
* Create a <kbd>library</kbd> folder with a file <kbd>update\_description.py</kbd> inside

<figure><img src="../../../.gitbook/assets/image (2).png" alt="" width="269"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

### Task 1: Find the correct RESTCONF path

* Use YANG Suite or yangcatalog.org, check the module `Cisco-IOS-XE-native` and the `:native/interface` path

### Task 2: Create the Ansible playbook

* Get interface list with RESTCONF (see Lab [204.-restconf](../204.-restconf/ "mention"), but check out the YANG path `Cisco-IOS-XE-native:native/interface` instead)
* Do something with the interface dictionary in a Python module (see Lab [205.-python-modules](../205.-python-modules/ "mention"), but pass in `restconf_result['json']` instead), return the interface dict to Ansible
* Update the interface list/description using RESTCONF with the returned interface dict
* 3 "extra" tasks could be "view result" tasks between each of your main tasks, for easier debugging

### Task 3: Create the Python module

* Use the example in the Ansible docs "Developing modules", or the module from the previous lab as an example [https://docs.ansible.com/ansible/latest/dev\_guide/developing\_modules\_general.html](https://docs.ansible.com/ansible/latest/dev_guide/developing_modules_general.html)
