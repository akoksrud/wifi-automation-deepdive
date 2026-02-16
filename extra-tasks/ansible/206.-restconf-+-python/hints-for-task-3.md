# Hints for Task 3

Now we are ready to write the Python module "update\_description.py". Lots of it will be identical to the previous Lab, but we have only one input parameter now. This will be the dictionary with the output from the RESTCONF call.

<figure><img src="../../../.gitbook/assets/image (13) (1) (1).png" alt=""><figcaption></figcaption></figure>

Then we do the actual reading and manipulation of the input

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

1. Put the input dictionary in a variable
2. Extract the description text. An intermediate step here could be to do a print() of the interface\_dict
3. Check if the text "Uplink" is in the description. If it is, we do nothing
4. If there is no "Uplink" text in the description, we create a new description text, including a timestamp
5. Then, we put the updated interface dictionary into the "result" dictionary, so Ansible can use it. Note here, that we put it under the key \['new\_interface\_dict'] which is where we extract it from in the Ansible playbook (line 53)

<figure><img src="../../../.gitbook/assets/image (16).png" alt="" width="529"><figcaption></figcaption></figure>



### Testing the RESTCONF Write operation in Postman

You can test the writing part in Postman

Here is the original configuration on the WLC:

<div align="left"><figure><img src="../../../.gitbook/assets/image (17).png" alt="" width="294"><figcaption></figcaption></figure></div>

Run the RESTCONF "PATCH" operation using Postman, you can experiment with various descriptions:

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Press "Send" and verify you get status 204

<div align="left"><figure><img src="../../../.gitbook/assets/image (20).png" alt="" width="85"><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="../../../.gitbook/assets/image (21).png" alt="" width="346"><figcaption></figcaption></figure></div>

Check the updated config on the WLC:\
![](<../../../.gitbook/assets/image (22).png>)



### Run the RESTCONF operation via Ansible

Ansible task, the outlined part is the variable that was updated using the Python module<br>

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

Show the original WLC config\
![](<../../../.gitbook/assets/image (23).png>)

Run the playbook<br>

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (26).png" alt="" width="563"><figcaption></figcaption></figure>

Show the updated WLC config<br>

<div align="left"><figure><img src="../../../.gitbook/assets/image (27).png" alt="" width="431"><figcaption></figcaption></figure></div>
