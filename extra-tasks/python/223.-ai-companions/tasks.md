# Tasks

### Task 1: Document the code

* Open one of the previous lab exercises. In this example we use the `get-client-table.py`
* Select all text in the .py file, click Ctrl+I, and write "create detailed documentation"

<figure><img src="../../../.gitbook/assets/image (8) (1).png" alt="" width="447"><figcaption></figcaption></figure>

### Task 2: Generate inline comments

* To improve readability, we can get AI to create inline comments
* Select all text in the .py file, click Ctrl+I, and write "create descriptive inline comments"

<figure><img src="../../../.gitbook/assets/image (2) (1) (1).png" alt="" width="447"><figcaption></figcaption></figure>

* You can follow-up and specify more by typing in the same box (GitHub Copilot) or selecting "Follow-up" (Windsurf), to get more detailed results etc.

<figure><img src="../../../.gitbook/assets/image (4) (1) (1).png" alt="" width="419"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (5) (1) (1).png" alt="" width="242"><figcaption></figcaption></figure>

### Task 3: See how generative AI would solve a previous task

* Check how AI would solve the task
* Create a new file `get-client-table-ai.py`
* In the empty file, Click Ctrl+I and type your prompt, it can be something similar to this

<figure><img src="../../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

* The result might be pretty similar to your script. Most AI companions will try to make new code similar to your open files/projects and use the same libraries etc. If you do this for an empty project/folder/instance or for something completely unrelated to what you have open, you might have more different results

### Task 4: Use AI to add or improve parts of the script

* Find some part to improve/change
* One example, enforce the user to input a valid IP address in the input part
* Mark the "Enter WLC IP" line, press Ctrl+I and type what you want the AI to help with

<figure><img src="../../../.gitbook/assets/image (7) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

* You might get something like this:

<figure><img src="../../../.gitbook/assets/image (8) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

* "ipaddress" is marked by Pylance since it is an unreferenced package. Import it in the beginning of the file if your AI assistant have not suggested it already

<figure><img src="../../../.gitbook/assets/image (9) (1).png" alt="" width="185"><figcaption></figcaption></figure>
