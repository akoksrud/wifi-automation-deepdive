# Initial config / installation

#### Installing Ubuntu Server

Frequent updates to Ubuntu can make the following pages somewhat different, but the basics should be recognizable. If you are asked to update the installer you can do this.

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

Choose your language and keyboard

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

To change keyboard layout later, you can run

```bash
sudo dpkg-reconfigure keyboard-configuration
```

Choose Ubuntu Server (you can also choose minimized, but might have to install some additional packages later)

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

Network configuration - choose DHCP for the initial installation unless you are installing directly into the network environment where you will have your server. In the "Day 1" tasks when you arrive at the deep dive and connect to the lab network, instructions will follow to change to a static IP

<figure><img src="../../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

Leave the proxy address blank

<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

Verify that the network is working and click Done when the tests are OK

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

Expand the disk usage to use the whole disk you have configured

1. In the first screen, choose "Use an entire disk" (default)

<figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

2. On the next screen, select "ubuntu-lv", then "Edit", and change "Size" to max value and Save

<figure><img src="../../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

On the next pages, just keep the defaults, and move on until you reach this page

<figure><img src="../../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

Install OpenSSH server. If you have your SSH public key on your GitHub account, you can select "Yes" on the "Import SSH identity" question, and enter your GitHub username in the box asking for that. If not, follow the instructions in [Git](https://app.gitbook.com/s/9qlH4foCfR5gDmwlHsV5/git "mention") to create and upload your key, either to the server directly or to your GitHub account.

<figure><img src="../../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

When you get to this screen, make sure to select **docker** as shown, then select "Done"

<figure><img src="../../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

After your first reboot, the login will look like this

<figure><img src="../../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

You should now be able to SSH into your server. It will make copy-paste of commands in the following sections possible (or at least easier). You can find the IP address of your Ubuntu Server using the following command

```bash
netplan status
```

From YOUR OWN COMPUTER, SSH into your Ubuntu Server IP with the "devnet-adm" username

```powershell
ssh devnet-adm@192.168.10.102
```

First, run the following commands to upgrade all packages to the latest version\
After that, make sure some essential tools are installed (should be)\
Then, add the current user to the docker group, to be able to run containers without sudo\
Finally, reboot your system

```bash
sudo apt update && sudo apt upgrade -y
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot
```
