# Hints for Task 1

### YANG Suite example

RESTCONF call for 9800:\
`https://`<mark style="color:orange;">`{host}`</mark>`/restconf/data/`<mark style="color:purple;">`{YANG module}`</mark>`:`<mark style="color:green;">`{xpath}`</mark> \
<mark style="color:orange;">host</mark>: 192.168.10.9 (change to YOUR WLC IP) \
<mark style="color:purple;">YANG module</mark>: Cisco-IOS-XE-crypto-pki-oper \
<mark style="color:green;">xpath</mark>: crypto-pki-oper-data/crypto-pki-bundle

https://<mark style="color:orange;">\{{host\}}</mark>/restconf/data/Cisco-IOS-XE-crypto-pki-oper:crypto-pki-oper-data/crypto-pki-bundle

<figure><img src="../../../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

### Yangcatalog.org example

* Use your browser to enter [https://yangcatalog.org](https://yangcatalog.org/)

<div align="left"><figure><img src="../../../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure></div>

* Click "YANG Module Detail Viewer"

<div align="left"><figure><img src="../../../.gitbook/assets/image (188).png" alt="" width="167"><figcaption></figcaption></figure></div>

* Start writing and then select the module. Click "Get details"

<div align="left"><figure><img src="../../../.gitbook/assets/image (189).png" alt="" width="460"><figcaption></figcaption></figure></div>

* Click "Tree View"

<div align="left"><figure><img src="../../../.gitbook/assets/image (190).png" alt="" width="108"><figcaption></figcaption></figure></div>

* Decide which level of data you want to retrieve. Let's start with the full bundle. You can click each line to expand or compact levels, or click the + next to "Element" to expand the full tree

<div align="left"><figure><img src="../../../.gitbook/assets/image (191).png" alt="" width="147"><figcaption></figcaption></figure></div>

* On the right hand of the "crypto-pki-bundle" line you will find the path you need in the "Sensor Path" column

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure></div>

* Copy the sensor path, and create the RESTCONF call:

<kbd>https://</kbd><kbd><mark style="color:orange;">\{{host\}}<mark style="color:orange;"></kbd><kbd>/restconf/data/Cisco-IOS-XE-crypto-pki-oper:crypto-pki-oper-data/crypto-pki-bundle</kbd>&#x20;



### Testing the RESTCONF path in Postman

* Enter the path in Postman

<figure><img src="../../../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure>

* You should hopefully get something like this, where you can see lots of details for each certificate on the device

<figure><img src="../../../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>

* To choose only a few fields, use the operator "?fields=" after the path. This example shows picking the label, subject-name and validity-end from above

<kbd>https://\{{host\}}/restconf/data/Cisco-IOS-XE-crypto-pki-oper:crypto-pki-oper-data/crypto-pki-bundle?fields=label;cert/subject-name;cert/validity-end</kbd>&#x20;

