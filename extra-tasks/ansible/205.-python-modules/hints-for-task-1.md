# Hints for Task 1

<figure><img src="../../../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure>

I have removed all the docs from the example, you could probably keep it

1. <mark style="color:blue;">module\_args</mark> should be "hostname" and "show\_run", both dict objects of type 'str'
2. <mark style="color:blue;">result</mark> should be dict, with <mark style="color:blue;">changed=False</mark> and nothing else
3. In the part where the actual "doing" is taking place, put stuff into result dict. You can add new key-value-pairs as you like
4. Take the hostname from input parameters, put it in the result dict, under result\['hostname']
5. Check if "restconf" is in the variable module.params\['show\_run']
6. If yes, put "True" in result\['restconf\_enabled']
7. If no, put "False" in result\['restconf\_enabled']
8. On exit, return the results back to Ansible





