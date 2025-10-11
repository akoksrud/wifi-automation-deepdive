# Tasks

### Task 0: Set up the files and folders and VS Code

* Create a working directory <kbd>python-get-client-table</kbd>
* Create a Python file <kbd>get-client-table.py</kbd>

<figure><img src="../../../.gitbook/assets/image (10) (1) (1).png" alt="" width="292"><figcaption></figcaption></figure>

* Remember to activate the automation-venv, it should show in the lower right corner of VS Code, and it should show at the beginning of the line in the terminal

<div align="center"><figure><img src="../../../.gitbook/assets/image (26) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="../../../.gitbook/assets/image (27) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

### Task 1: Use Postman to find and test an URL that gives you the connected clients

* Use YANG Suite or yangcatalog.org to find the correct path
* Use Postman to test the RESTCONF path
* Use [142.-prepare-restconf-calls.md](../../../main-tasks/python/142.-prepare-restconf-calls.md "mention") for reference

### Task 2: Write a Python script that

* Ask for WLC IP, username and password
* Connects to the WLC using RESTCONF with the URL created in Task 1
* Print the results

### (optional) Task 3: Extend the script with

* Check if response status code is 200, if not, show the status code and message
* Flatten the JSON of the response to a table, store in a pandas dataframe
* Save the dataframe to Excel
