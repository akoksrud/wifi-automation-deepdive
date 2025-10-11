# Hints for Task 2

1. Start by creating the task that gets the data from WLC, using the RESTCONF path we have tested in Postman

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure></div>

2. Create a simple "view" task, to easier understand and debug what we have got out. Only if the status code = 200.

<figure><img src="../../../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png" alt="" width="319"><figcaption></figcaption></figure>

3. Create a task that will send the interface dictionary (in JSON format) to our Python module for processing. Only run this if (`when:` ) the status code from our RESTCONF call equals 200 ("OK")

<figure><img src="../../../.gitbook/assets/image (9) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

4. Create a simple "view" task to view the results/output of the Python module processing, which we have registered in the variable "update\_description\_result". And again, only if the result of the original RESTCONF call was "200 OK"

<figure><img src="../../../.gitbook/assets/image (10) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

5. The last part of the playbook, you might want to write after or in parallel with writing the Python module as it includes using the output from the module. We create the final of our three primary tasks for this playbook, updating the WLC interface description using RESTCONF

{% hint style="info" %}
Notice that the use of the uri module is similar to the read task, only using PATCH instead of GET, and actually having some data in the "body" field. What we put in there is based on what we got out, only modified in the Python module which we will look into next
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>

6. As usual, we have a "view" task to check the output

<figure><img src="../../../.gitbook/assets/image (12) (1) (1).png" alt="" width="428"><figcaption></figcaption></figure>

