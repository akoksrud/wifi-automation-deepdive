# Example solution

<figure><img src="../../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

1. Create the API URL
2. Do the actual RESTCONF call
3. Check if response status code is 200. If not, show the status code and message
4. Flatten the JSON of the response to a table, store in a pandas dataframe
5. Save the dataframe to Excel

{% code title="get-glient-table.py" %}
```python
import requests
import getpass
import pandas as pd

wlc = input("Enter WLC IP: ")
user = input("Enter user: ")
password = getpass.getpass("Enter password: ")
url = f"https://{wlc}/restconf/data/Cisco-IOS-XE-wireless-client-oper:client-oper-data/common-oper-data"
payload = {}
headers = {
  'Accept': 'application/yang-data+json',
  'Content-Type': 'application/yang-data+json'
  }

response = requests.get(url, auth=(user, password), headers=headers, data=payload, verify=False)

if (response.status_code==200):
    ap_table = pd.json_normalize(response.json()['Cisco-IOS-XE-wireless-client-oper:client-oper-data'])
    print(ap_table)
    ap_table.to_excel('ap_table.xlsx')
else:
    print(f"Status code: {response.status_code}: {response.reason}")

```
{% endcode %}
