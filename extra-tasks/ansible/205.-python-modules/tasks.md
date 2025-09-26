# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>ansible-module</kbd>
* Create a playbook file <kbd>module-playbook.yml</kbd>&#x20;
* Copy the <kbd>hosts.yml</kbd> file from the previous tasks
* Create a <kbd>library</kbd> folder with a file <kbd>check\_restconf\_status.py</kbd> inside
* Create a <kbd>logs</kbd> folder where we will dump some logs later

<figure><img src="../../../.gitbook/assets/image (197).png" alt="" width="269"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

### Task 1: Create the Python module

* Use the example in the Ansible docs "Developing modules" as an example\
  [https://docs.ansible.com/ansible/latest/dev\_guide/developing\_modules\_general.html](https://docs.ansible.com/ansible/latest/dev_guide/developing_modules_general.html)

### Task 2: Create the Ansible playbook

* The playbook should have 3 tasks
  * Gather IOS facts (check docs on the cisco.ios.ios\_facts module, [https://docs.ansible.com/ansible/latest/collections/cisco/ios/ios\_facts\_module.html#ansible-collections-cisco-ios-ios-facts-module](https://docs.ansible.com/ansible/latest/collections/cisco/ios/ios_facts_module.html))
  * Run your module, it should be called the same way as a regular module, and the arguments indented below the module
  * Write the results to a YAML file
