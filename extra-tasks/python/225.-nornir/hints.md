# Hints

In the .env file, we only put the username and password this time

{% code title=".env" %}
```
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

For the runbook "python\_nornir\_runbook.py":

* Reuse the dotenv import and env = dotenv\_values('.env') from [224.-using-.env-files](../224.-using-.env-files/ "mention")
* Import some Nornir stuff that we need

<figure><img src="../../../.gitbook/assets/image (228).png" alt=""><figcaption></figcaption></figure>

* Initialize Nornir

```python
nr = InitNornir()
```

* Set some Nornir defaults

```python
nr.inventory.defaults.username= #(Get this from env['USERNAME'])
nr.inventory.defaults.password= #(Get this from env['PASSWORD'])
nr.inventory.defaults.platform="ios"
```

* Run commands and save the output in "results"

```python
results = nr.run(
    task = netmiko_send_command
    command_string = "show ap summary"
)
```

* Print "results" using Nornir

```python
print_result(results)
```
