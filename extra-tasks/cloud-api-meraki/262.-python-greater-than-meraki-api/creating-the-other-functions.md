# Creating the other functions

Do the same for `show_device_summary()` \
Use `getOrganizationDevices` from Postman \
Change the Organization Id from Postman with `{organizationId}` from .env

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Do the same for `show_client_summary()` \
Use `getNetworkClients` from Postman \
Change the Network ID from Postman with `{networkId}` from .env

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Do the same for `show_cdp_neighbors()` \
Use `getDeviceLldpCdp` from Postman \
Change the S/N from Postman with `{serial}` from .env

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Some suggestions for next steps could be

* Print the JSON output more pretty, you can use pretty-print (from pprint import pprint)
* Save the JSON to a JSON file (use the method from [224.-using-.env-files](../../python/224.-using-.env-files/ "mention") where you saved run-config)
* Flatten the JSON output to a pandas dataframe and save to CSV or Excel (From [222.-get-client-table](../../python/222.-get-client-table/ "mention"))

