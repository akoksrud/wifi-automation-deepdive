# Creating the Python script

Create a new folder `meraki-python`&#x20;

Copy the "get-client-table.py" from [224.-using-.env-files](../../python/224.-using-.env-files/ "mention") where we have a simple menu structure, and use a .env file. Rename it to "meraki-script.py"

<figure><img src="../../../.gitbook/assets/image (4).png" alt="" width="201"><figcaption></figcaption></figure>

Create a .env file, and fill inn your values from the Postman part of the lab

<figure><img src="../../../.gitbook/assets/image (5).png" alt="" width="308"><figcaption></figcaption></figure>

{% code title=".env" %}
```python
apiKey='{YOUR TOKEN}'
orgId='{YOUR Org ID}'
networkId='{YOUR Network ID}'
serial='{YOUR DEVICE SERIAL}'
```
{% endcode %}

Read the values from the .env file into variables in your Python script

<figure><img src="../../../.gitbook/assets/image (7).png" alt="" width="416"><figcaption></figcaption></figure>

Modify the script to use some modified functions, and show some modified text

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Here is an example of a "empty" script. All the functions are just printing the headline. Next we will write the RESTCONF calls to the Meraki cloud

{% code title="meraki-script.py" %}
```python
from dotenv import dotenv_values

# Import variables from the .env file
env = dotenv_values('.env')
apiKey = env['apiKey']
organizationId=env['orgId']
networkId=env['networkId']
serial=env['serial']

# Define functions
def show_device_summary():
    print('Device summary:\n-------------------------------------')

def show_client_summary():
    print('Client summary:\n-------------------------------------')

def show_cdp_neighbors():
    print(f"CDP neighbors for device {serial}:\n-------------------------------------")
    
def get_device_dhcp_subnets():
    print(f"DHCP subnets for device {serial}:\n-------------------------------------")
    
# Text menu with 4 options that run each of the functions, or quit
while True:
    print(f'\nYou are connected to organization {organizationId} and network {networkId}')
    print("Menu:")
    print("1. Show Device summary")
    print("2. Show client summary")
    print("3. Show CDP neighbors")
    print("4. Show DHCP subnets")
    print("5. Quit")

    choice = input("Enter choice: ")

    if choice == "1":
        show_device_summary()
    elif choice == "2":
        show_client_summary()
    elif choice == "3":
        show_cdp_neighbors()
    elif choice == "4":
        get_device_dhcp_subnets()
    elif choice == "5":
        break
    else:
        print("Invalid choice. Please choose again.")

```
{% endcode %}
