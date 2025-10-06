# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>ansible-import-playbook</kbd>
* Create a playbook file <kbd>audit-network-playbook.yml</kbd>
* Create a folder <kbd>audit\_playbooks</kbd> with three playbooks
  * <kbd>audit-routers-playbook.yml</kbd>
  * <kbd>audit-switches-playbook.yml</kbd>
  * <kbd>audit-wlcs-playbook.yml</kbd>

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1) (1) (1).png" alt="" width="335"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>



### Task 1: Create an extended hosts.yml file

* The inventory should include
  * Shared switch (192.168.10.2)
  * Your WLC (192.168.10.{YOUR\_WLC\_IP})
  * One or more other WLCs

### Task 2: Create the three playbooks in the "audit\_playbooks" folder

* They should be simple playbooks, use what you have learned. The example use two tasks:
  * Gather IOS facts (using cisco.ios.ios\_facts module)
  * Output hostname and version (using ansible.builtin.debug module and prints text from the facts)

### Task 3: Create the audit-network-playbook.yml&#x20;

* This playbook is used to run the other three playbooks&#x20;
* Use the ansible.builtin.import\_playbook module
