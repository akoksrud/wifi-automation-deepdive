# Hints for Task 3

Task 3 was to rewrite the menu elements. The old menu started by showing the (one) WLC you were connected to. For the Nornir variant we can be connected to lots of WLCs, so we have to adjust the menu accordingly.

Old WLC connection info:

```python
    print('\nYou are connected to WLC: ' + env['WLC_IP'])
```

New WLC connection info:

```python
    print('\nYou are connected to these devices: ')
    for host in nr.inventory.hosts:
        print(f'-> {host}: {nr.inventory.hosts[host].hostname}')
```

In this example, you loop over the hosts found in the Nornir inventory (`nr.inventory.hosts`), and call the element in each of your loop interations `host`

In the next line you use an f-string, and print the text of the host, along which the hostname found in the Nornir inventory, in our case the "hostname" will be the IP address of the device

This info corresponds to what you have written in the `hosts.yaml` file, so for our example inventory:

{% code title="hosts.yaml" %}
```yaml
---
your_wlc:
   hostname: 192.168.10.10
shared_wlc:
   hostname: 192.168.10.9
```
{% endcode %}

... we should get the following header of the menu system:

<div align="left"><figure><img src="../../../.gitbook/assets/image (231).png" alt="" width="350"><figcaption></figcaption></figure></div>



