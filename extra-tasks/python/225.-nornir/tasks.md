# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>python-nornir</kbd>
* Create a <kbd>.env</kbd> file (similar to [224.-using-.env-files](../224.-using-.env-files/ "mention") )
* Create a <kbd>hosts.yaml</kbd> file
* Create a Python file <kbd>python-nornir-runbook.py</kbd> . You can reuse the dotenv parts from [224.-using-.env-files](../224.-using-.env-files/ "mention")

<figure><img src="../../../.gitbook/assets/image (227).png" alt="" width="281"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

### Task 1: Install Nornir in your venv

```bash
uv pip install nornir nornir-utils nornir-netmiko
```

### Task 2: Create inventory file

* This exercise will use a very simple hosts.yaml file for inventory, with only the devices and the device type.&#x20;
* Username and password will come from the .env file

### Task 3: Write a runbook that

* Connects to all devices in the inventory
* Do a "show ap summary"
* Print the results on screen
