# Hints for Task 1

In the .env file, we only put the username and password

{% code title=".env" %}
```yaml
USERNAME='devnet-adm'
PASSWORD='ChangeMe2025!'
```
{% endcode %}

In the hosts.yml we put the WLC IP, you can easily scale this to multiple devices

{% code title="hosts.yaml" %}
```yaml
---
your_wlc:
   hostname: 192.168.10.{YOUR_WLC_IP}

shared_wlc:
   hostname: 192.168.10.9
```
{% endcode %}

Add the Nornir imports, remove the Netmiko imports

<figure><img src="../../../.gitbook/assets/image (5).png" alt="" width="563"><figcaption></figcaption></figure>

Initialize Nornir and set the defaults

<figure><img src="../../../.gitbook/assets/image (6).png" alt="" width="563"><figcaption></figcaption></figure>

Remove the Netmiko initialization

<figure><img src="../../../.gitbook/assets/image (7).png" alt="" width="418"><figcaption></figcaption></figure>
