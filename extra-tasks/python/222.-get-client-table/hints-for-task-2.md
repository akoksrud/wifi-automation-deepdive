# Hints for Task 2

* Write a Python script that
  * Ask for WLC IP, username and password
  * Connects to the WLC using RESTCONF with the URL created in Task 1
  * Print the results
* The input part of this script you can reuse from the netmiko script in [221.-netmiko](../221.-netmiko/ "mention")
* The RESTCONF connection will use the "requests" module. You should be able to get some hints from Postman, "output to code" and choose Python
* To create the URL including the WLC IP, you can use f-strings, like this:

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* You can end/check this task by using a print statement after the requests call

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* Remember the imports (and maybe you need some `uv pip install` along the way)

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1).png" alt="" width="163"><figcaption></figcaption></figure>
