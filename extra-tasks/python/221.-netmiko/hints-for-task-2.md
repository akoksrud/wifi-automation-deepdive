# Hints for Task 2

Building on the work from Task 1, we add user/pass input

<div align="left"><figure><img src="../../../.gitbook/assets/image (209).png" alt="" width="458"><figcaption></figcaption></figure></div>

Now, we will make Netmiko connect and run a command

* import the ConnectHandler function from Netmiko

<div align="left"><figure><img src="../../../.gitbook/assets/image (210).png" alt="" width="416"><figcaption></figcaption></figure></div>

* Create a "cisco\_wlc" dictionary which ConnectHandler use as input

<div align="left"><figure><img src="../../../.gitbook/assets/image (212).png" alt="" width="476"><figcaption></figcaption></figure></div>

* Create a "command" variable, which we print, and send to the WLC

<div align="left"><figure><img src="../../../.gitbook/assets/image (213).png" alt="" width="467"><figcaption></figcaption></figure></div>

Example output from running the script so far:

<div align="left"><figure><img src="../../../.gitbook/assets/image (214).png" alt="" width="468"><figcaption></figcaption></figure></div>
