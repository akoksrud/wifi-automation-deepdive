# Example solution

### Example .env file

{% code title=".env" %}
```
USERNAME='devnet-adm'
PASSWORD='ChangeMe2025!'
```
{% endcode %}

### Example hosts file

* Swap `{YOUR_WLC_IP}` with your designated WLC IP

{% code title="hosts.yaml" %}
```yaml
---
your_wlc:
   hostname: 192.168.10.{YOUR_WLC_IP}

shared_wlc:
   hostname: 192.168.10.9

```
{% endcode %}

### Example Runbook

{% code title="python-nornir-runbook.py" %}
```yaml
from dotenv import dotenv_values
from nornir import InitNornir  # Initialize Nornir
from nornir_utils.plugins.functions import print_result  # Print results
from nornir_netmiko.tasks import netmiko_send_command  # Send Netmiko command

# Import variables from the .env file
env = dotenv_values('.env')

# Initialize Nornir
nr = InitNornir()

# Set defaults for all devices
nr.inventory.defaults.username = env['USERNAME']  # Username from .env
nr.inventory.defaults.password = env['PASSWORD']  # Password from .env
nr.inventory.defaults.platform="ios"  # Platform set to Cisco IOS

# Run command on all devices
results = nr.run(
    task=netmiko_send_command,  # Use the task "netmiko_send_command"
    command_string="show ap summary"  # Command to run
)

# Print results
print_result(results)

```
{% endcode %}

### Example output

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure></div>

* As long as you use `hosts.yaml` you don't have to specify this anywhere, as it is the default inventory file that Nornir will look for, in the folder you run the script from
* You can use a dynamically created inventory, here are some examples
  * Service-Now can pass an inventory when you run stuff based on something you pass from there
  * You can use Netbox for inventory, and filter/pass/extract what you want from there. Like, if you get an action because an AP is down, run some checks on the switch and the WLC the AP was connected last. And some checks on all APs on the same location. Etc.
