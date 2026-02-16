# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory `ansible-roles`
* Create a playbook file `audit-network-playbook.yml`
* Create a folder `get_max_aps` and a subfolder `tasks` which contains a playbook `main.yml`
* Create a folder `get_version` and a subfolder `tasks` which contains a playbook `main.yml`&#x20;
* Copy the `hosts.yml` from the previous exercise

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1) (1).png" alt="" width="296"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>



### Task 1: Create the audit-network-playbook.yml content

* Playbook task 1: Get version from all Cisco devices, for "all" hosts, using the roles "get\_version"
* Playbook task 2: Get max APs from WLCs, for "wlc" hosts, using the roles "get\_max\_aps"

### Task 2: Create the role get\_version

* Edit the main.yml in the get\_version/tasks folder. It should have two tasks:
  * Gather IOS facts. Reuse from [115.-exercise-gather-facts.md](../../../main-tasks/ansible/115.-exercise-gather-facts.md "mention"), but only the task, not the playbook stuff before the task. You will need to de-indent this to avoid indentation errors since you drop the "outer layer" in the yaml file
  * Ouput task, use the ansible.builtin.debug module instead of writing to file as you did in [115.-exercise-gather-facts.md](../../../main-tasks/ansible/115.-exercise-gather-facts.md "mention"). You can narrow down the output to only ansible\_net\_hostname and ansible\_net\_version with some enclosing text

### Task 3: Create role get\_max\_aps&#x20;

* Edit the main.yml in the get\_max\_aps/tasks folder. It should have two tasks:
  * Gather Max APs supported. Reuse from [201.-run-cli-commands](../201.-run-cli-commands/ "mention"), but only the task, not the playbook stuff before the task. You will need to de-indent this to avoid indentation errors since you drop the "outer layer" in the yaml file
  * Ouput task, use the ansible.builtin.debug module, you can print the \{{ result.stdout \}} message
