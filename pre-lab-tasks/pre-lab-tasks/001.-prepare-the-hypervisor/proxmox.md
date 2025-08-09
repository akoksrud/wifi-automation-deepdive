# Proxmox

{% hint style="info" %}
Proxmox is our recommendation if you will run the VMs on a separate server (not your work laptop). The pre-configured VMs in this lab run on multiple proxmox servers
{% endhint %}

## Installing Proxmox

Follow the installation instructions on [https://proxmox.com](https://proxmox.com/) under Products -> Proxmox Virtual Environment -> Get Started:

[https://proxmox.com/en/products/proxmox-virtual-environment/get-started](https://proxmox.com/en/products/proxmox-virtual-environment/get-started)

1. Download the ISO
2. Create a bootable USB flash drive from the ISO (examples of software to use is Rufus or Balena Etcher)
3. Boot the server from the USB stick
4. Configure the server

Full instructions on how to install Proxmox, or to troubleshoot this, is outside the scope of this lab guide. Note that Proxmox will use the whole disk, and erase everything that was present before.

For production use, licenses should be aquired. For lab work, support won't be that critical, so you could run without license. Proxmox itself is open source, but the company earns their well deserved cash by offering various levels of support agreements/licensing. You will get this box each time you log in to to the Proxmox web page

<figure><img src="../../../.gitbook/assets/image (35) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Configure repositories

To be able to update the proxmox server you must configure the relevant repositories. If you have aquired a license it will be preconfigured correctly, but for the open source license-free variant you will have to enable a "no subscription" repo.

1. Go to your node {server name} -> Updates -> Repositories

<figure><img src="../../../.gitbook/assets/image (36) (1) (1).png" alt=""><figcaption></figcaption></figure>

2. Add the "No-Subscription" repository

<figure><img src="../../../.gitbook/assets/image (37) (1) (1).png" alt=""><figcaption></figcaption></figure>

3. Disable the two Enterprise repositories

<figure><img src="../../../.gitbook/assets/image (38) (1) (1).png" alt=""><figcaption></figcaption></figure>

3. You can then update from GUI or from CLI

```bash
root@proxmox5:~$ apt update
root@proxmox5:~$ apt upgrade
```

## Download Ubuntu Server

Go to [https://ubuntu.com/download/server](https://ubuntu.com/download/server)

<figure><img src="../../../.gitbook/assets/image (10) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Click "Download 24.04 LTS"</p></figcaption></figure>

## Create the VM

Open the Proxmox website [http://{proxmox-ip}:8006/](http://{proxmox-ip}:8006/)

Start by uploading the Ubuntu Server ISO to the Proxmox datastore:\
Datacenter > proxmox > local (proxmox)\
Select "ISO images" and "Upload"

<figure><img src="../../../.gitbook/assets/image (39) (1).png" alt=""><figcaption></figcaption></figure>

Right-click your proxmox node and select "Create VM"

<figure><img src="../../../.gitbook/assets/image (40) (1).png" alt=""><figcaption></figcaption></figure>

Set the name and if it should start on boot

<figure><img src="../../../.gitbook/assets/image (41) (1).png" alt=""><figcaption></figcaption></figure>

Under "OS", select the ISO image

<figure><img src="../../../.gitbook/assets/image (42) (1).png" alt=""><figcaption></figcaption></figure>

Under System, keep the defaults

<figure><img src="../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Under Disks, change to 40 GiB

<figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

Under CPU, keep the defaults

<figure><img src="../../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

Under Memory, change to 4096 MiB

<figure><img src="../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

Under "Network", select vmbr0

<figure><img src="../../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

Start your machine

<figure><img src="../../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

Connect to the console of your VM to install the OS

<figure><img src="../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

Skip the chapters for the other hypervisors, continue from the "Configure Ubuntu Server" chapter&#x20;

{% content-ref url="../002.-configure-ubuntu-server/" %}
[002.-configure-ubuntu-server](../002.-configure-ubuntu-server/)
{% endcontent-ref %}
