# Hints for Task 1

Start with the print command, printing a static text

<div align="left"><figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt="" width="341"><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1).png" alt="" width="417"><figcaption></figcaption></figure></div>

Then add the input, which is saved to a variable "wlc\_ip"

<div align="left"><figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt="" width="377"><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt="" width="417"><figcaption></figcaption></figure></div>

Notice the "f-string" formatting of the printed text. This is widely used in Python to use variables inside strings.

To keep this short and simple, we have no error checking. So the "IP" you enter could just as well be "blablabla"

<div align="left"><figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1) (1) (1).png" alt="" width="417"><figcaption></figcaption></figure></div>

This will be the case in most of these labs, it is by design

Depending on the usage of your script, you should probably add some error checking, especially if used by others. One example would be to use regex to check if the value is a correct IP address, so the output could be like this

<div align="left"><figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt="" width="417"><figcaption></figcaption></figure></div>

Another even more "production ready" approach would be to use an IP Address class or similar, to ensure correct formatting, immutable values, proper printing and conversion etc.
