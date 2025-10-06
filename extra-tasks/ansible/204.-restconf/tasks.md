# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>ansible-restconf</kbd>
* Create a playbook file <kbd>restconf-playbook.yml</kbd>&#x20;
* Copy the <kbd>hosts.yml</kbd> file from the previous tasks

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="281"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

### Task 1: Use YANG Suite (or yangcatalog.org) to find the RESTCONF path that will give details about the certificates

* Load and view the details of the module "Cisco-IOS-XE-crypto-pki-oper"
* Test the RESTCONF call towards your WLC with Postman
* Add some filters, to only return the label, subject-name and validity-end

### Task 2: Write the Ansible task to use your RESTCONF path

* Use the "ansible.builtin.uri" module to perform the RESTCONF call
* Print the results of the call
* Print the results of just the validity date of each result

