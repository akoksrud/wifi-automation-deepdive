# VirtualBox

{% hint style="info" %}
VirtualBox is only recommended if you can not run Hyper-V (Win) or Multipass (Mac)
{% endhint %}

## Installing VirtualBox

Download from [https://virtualbox.org/](https://virtualbox.org/)

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

* You will need admin privileges to install VirtualBox
* Not all steps are shown here, it is mostly "next-next-next"
* As a default folder for VMs, I use "C:\Virtual Machines". You can use whatever you like, but screenshots here will show that path

## Creating a virtual switch

In VirtualBox, a bridged/external switch is available without further configuration.  This will connect the adapter of your virtual machine on the same network as your Ethernet adapter, and it will get an IP address on the same network.

## Download Ubuntu Server

Go to [https://ubuntu.com/download/server](https://ubuntu.com/download/server)

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Click "Download 24.04 LTS"</p></figcaption></figure>

## Create the VM

Open VirtualBox

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Machine -> New...

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Configure the following:\
1\. Name, folder and select the ISO that you downloaded\
2\. Select type "Linux", Subtype "Ubuntu" and Version "Ubuntu (64-bit)"\
3\. Check "Skip Unattended Installation"

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

4. Expand the «Hardware» section. Increase Base Memory to 4096MB

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

5. Expand the «Hard Disk» section. Increase to 40GB, then Finish

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Select your newly created VM in the list, then click "Settings"

<figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

In the "System" tab, uncheck "Floppy"

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

In the "Display" tab, ensure "Video Memory" is at least 30MB. Keep the rest at default.

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

In the "Storage" tab, no change is needed

In the "Audio" tab, remove the "Enable Audio" checkbox

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

In the "Network" tab, select:\
1\. Attached to: Bridged Adapter\
2\. Name: Select your Ethernet adapter\
3\. Keep the rest as default, and do not enable adapter 2, 3 or 4 on their respective tabs

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

Click "OK" to save the changes

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

Start your machine\
As a dropdown from the "Start" button you can also choose "Headless start". When you have given your VM a static IP so you can connect to it using SSH, this would be your preferred choice.

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

Skip the chapters for the other hypervisors, continue from the "Configure Ubuntu Server" chapter&#x20;

{% content-ref url="../002.-configure-ubuntu-server/" %}
[002.-configure-ubuntu-server](../002.-configure-ubuntu-server/)
{% endcontent-ref %}
