# 224. Using .env files

As an alternative to typing the WLC IP, username and password every time, they can be placed in a local file with the name ".env". This is one method to share the python script without including sensitive material in the script itself

\
We will modify the "netmiko-script.py" from Lab 40, by adding support for reading the .env file. The contents of the script (except for those modifications), are already explained in Lab 40<br>

Remember that the .env file should be located in the same directory as you run the file from<br>

{% hint style="info" %}
`.env` files are usually NOT synced by Git, they are included in a `.gitignore` file. This is by purpose, and is WHY we are using `.env` files instead of writing stuff in cleartext in the code. So if you look in the "solutions" folder, there will be no .env files in this or any other directory, you must create your own.

The `.gitignore` file is usually created when you initialize the git repo, make sure that you exclude any files you don't want to be included in the sync.

A common practice is to include an example file that IS synced to your repo, like `env.example` or similar. There you can have placeholder values like USERNAME='dummy'
{% endhint %}
