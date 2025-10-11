# Filling in the first function

Merge the code snippet from Postman into the function show\_device\_dhcp\_subnets()

* Import the requests package (top of file)

<div align="left"><figure><img src="../../../.gitbook/assets/image (8).png" alt="" width="167"><figcaption></figcaption></figure></div>

* Write the rest into the get\_device\_dhcp\_subnets() function&#x20;
* We change the url with an f-string and put in the variable "serial" from the .env file instead
* Instead of the Authorization in the Postman example, we use the key "X-Cisco-Meraki-API-Key" and use apiKey from the .env file as the value

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Here is how it looks in Postman

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>





