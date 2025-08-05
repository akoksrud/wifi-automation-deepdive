# Git clone the example files

The Wi-Fi automation deep dive are hosted on GitHub as a public repository. We will download the contents, including example files and solutions, to our Ubuntu Server. Other than that, Git is not used for version control or backup in this lab. However, it is highly recommended that you learn some basic use of Git to backup and version control your own projects. GitHub account is free, and you can create a private repository (that only you can access, but don't use it for highly classified stuff)

```bash
cd ~
git clone https://github.com/akoksrud/wifi-automation
cd wifi-automation
ls -l
```

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

To update the contents of a cloned repository, enter the direcory and do a "git pull" like this

```bash
git pull origin main
```

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
