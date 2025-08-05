# Multipass

{% hint style="info" %}
Multipass is our recommendation if you will run the VMs on your Macbook
{% endhint %}

## Installing Multipass

Visit the following link for instructions on installing Multipass on Mac:

[https://canonical.com/multipass/docs/install-multipass](https://canonical.com/multipass/docs/install-multipass)

Select "macOS" in the drop down menus to get the Mac install instructions

<figure><img src="../../../.gitbook/assets/image (34) (1) (1).png" alt=""><figcaption></figcaption></figure>

Full instructions on how to install Multipass, or to troubleshoot this, is outside the scope of this lab guide.&#x20;

## Verify that Multipass is installed and working

```bash
akoksrud:MacOS ~$ multipass --version
multipass   1.15.0+mac
multipassd  1.15.0+mac
```

## Other commands

```bash
akoksrud:MacOS ~$ multipass list
Name            State           IPv4             Image
ubuntu-devnet   Running         192.168.64.9     Ubuntu 24.04 LTS
akoksrud:MacOS ~$ multipass launch --name ubuntu-devnet
akoksrud:MacOS ~$ multipass start ubuntu-devnet
akoksrud:MacOS ~$ multipass shell ubuntu-devnet
akoksrud:MacOS ~$ multipass stop ubuntu-devnet
akoksrud:MacOS ~$ multipass delete ubuntu-devnet
akoksrud:MacOS ~$ multipass purge
```

## Configure networking

Instruct Multipass to use your wired adapter as a bridge adapter. In this example the Mac have two wired ethernet adapters, we will use one of them

```bash
akoksrud:MacOS ~$ multipass networks
Name    Type       Description
en0     wifi       Wi-Fi
en4     ethernet   Ethernet Adapter (en4)
en5     ethernet   Ethernet Adapter (en5)

akoksrud:MacOS ~$ multipass set local.bridged-network=en4
```

## Download Ubuntu Server

Go to[ https://ubuntu.com/download/server/arm](https://ubuntu.com/download/server/arm)

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Create the VM

Create a folder for your VM

```bash
akoksrud@MacOS:~/$ mkdir ubuntu-devnet
akoksrud@MacOS:~/$ cd ubuntu-devnet
akoksrud@MacOS:~/ubuntu-devnet$ 
```

Create a file named "cloud-config.yaml". You can use any editor of choice.

```
akoksrud@MacOS:~/ubuntu-devnet$ nano cloud-config.yaml
```

Enter the following contents in the cloud-config.yaml file and save it

```yaml
users:
  - default
  - name: devnet-adm
    lock_passwd: false
    sudo: ALL=(ALL) NOPASSWD:ALL
    plain_text_passwd: ChangeMe2025!
    shell: /bin/bash
ssh_pwauth: True
package_update: true
package_upgrade: true
```

From the same folder you created the YAML file, create the server using the following command

{% code fullWidth="false" %}
```bash
akoksrud@MacOS:~/ubuntu-devnet$ multipass launch --name ubuntu-devnet --bridged --memory 4G --disk 40G --cpus 2 --cloud-init cloud-config.yaml
Creating ubuntu-devnet /
Configuring ubuntu-devnet /
Starting ubuntu-devnet /
```
{% endcode %}

List your VMs, it should show the newly created VM

```bash
akoksrud@MacOS:~/ubuntu-devnet$ multipass list
Name            State           IPv4             Image
ubuntu-devnet   Running         192.168.10.163   Ubuntu 24.04 LTS
```

Show VM info

```bash
akoksrud@MacOS:~/ubuntu-devnet$ multipass info ubuntu-devnet
Name:           ubuntu-devnet
State:          Running
(…)
```

You can connect to your server using the "multipass shell" command

```bash
akoksrud@MacOS:~/ubuntu-devnet$ multipass shell ubuntu-devnet
Welcome to Ubuntu 24.04.1 LTS (GNU/Linux 6.8.0-51-generic x86_64)
(…)
ubuntu@ubuntu-devnet:~$ exit
```

You can also connect using SSH and your IP address

```bash
akoksrud@MacOS:~/ubuntu-devnet$ ssh devnet-adm@192.168.10.163
devnet-adm@192.168.10.163's password: ChangeMe2025!
Welcome to Ubuntu 24.04.1 LTS (GNU/Linux 6.8.0-51-generic x86_64)
(…)
ubuntu@ubuntu-devnet:~$ exit
```

Skip the chapters for the other hypervisors, continue from the "Configure Ubuntu Server" chapter&#x20;

**Note**: Most of the server installation will be done by Multipass and the cloud-init process. But make sure to do the following steps

* Change keyboard layout
* Change to static IP
* Create and import SSH key
* Clone the example Git repository

Skip the chapters for the other hypervisors, continue from the "Configure Ubuntu Server" chapter&#x20;

{% content-ref url="../002.-configure-ubuntu-server/" %}
[002.-configure-ubuntu-server](../002.-configure-ubuntu-server/)
{% endcontent-ref %}
