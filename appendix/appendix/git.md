# Git

### Prerequisites

You must have Git installed for this part to work.

Windows

```powershell
winget install Git.Git
```

Mac

```powershell
brew install git
```

Ubuntu

```powershell
sudo apt install git
```

### Git config

Start by setting your name and email (change to your Git username and email accordingly)

```bash
git config --global user.name "akoksrud"
git config --global user.email "andreas@koksrud.no"
```

If you have a SSH key, you can enable signed commits using that key

```bash
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global gpg.format ssh
git config --global commit.gpgsign true
```

### Upload SSH key

See the following link for uploading the public SSH key to your GitHub account: [https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

The core contents of GitHub's guide are listed here:

1. Login to GitHub
2. In the upper-right corner of any page on GitHub, click your profile picture, then click **Settings**.
3. In the "Access" section of the sidebar, click **SSH and GPG keys**.
4. Click **New SSH key** or **Add SSH key**.
5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal laptop, you might call this key "Personal laptop".
6. Select the type of key, either authentication or signing. You can add the same key for both purposes. For more information about commit signing, see [About commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification).
7. In the "Key" field, paste your public key.
8. Click **Add SSH key**.
9. If prompted, confirm access to your account on GitHub. For more information, see [Sudo mode](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/sudo-mode).

It will look something like this:

<figure><img src="../../.gitbook/assets/image (162).png" alt=""><figcaption></figcaption></figure>
