# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>python-nornir-extended</kbd>
* Create a <kbd>.env</kbd> file (copy from [225.-nornir](../225.-nornir/ "mention"))
* Create a <kbd>hosts.yaml</kbd> file (copy from [225.-nornir](../225.-nornir/ "mention"))
* Create a Python file <kbd>python-nornir-extended-runbook.py</kbd> . Start by copy-pasting the <kbd>netmiko-script.py</kbd> from [221.-netmiko](../221.-netmiko/ "mention")

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt="" width="281"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

### Task 1: Add Nornir components to the runbook

Merge what you learned in the previous exercise ([225.-nornir](../225.-nornir/ "mention")) into the runbook, which should start out as a copy of `netmiko-script.py` from [221.-netmiko](../221.-netmiko/ "mention"). We will use Nornir instead of Netmiko to connect to the devices

* Add Nornir stuff
  * Add Nornir imports
  * Set Nornir defaults
  * Initialize Nornir
* Remove Netmiko stuff
  * Remove Netmiko imports
  * Remove definition of cisco\_wlc object
  * Remove initializing net\_connect = ConnectHandler()

### Task 2: Rewrite the functions that are called from the menu

The functions called from the menu, should use nornir\_netmiko and use the Nornir inventory

* All lines referring to "net\_connect" needs to be changed

### Task 3: Rewrite the menu

The section "You are connected to" should now show all devices from the inventory that you will issue the commands to
