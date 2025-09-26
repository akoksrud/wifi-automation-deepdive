# 206. RESTCONF + Python

This is another exercise where we create our own Python module to do some "magic" with output from Ansible, and return them back to Ansible after being processed

We will combine this with using RESTCONF directly from Ansible, as this is very fast compared to getting the same results using the command line

By "very fast" that refers to the run-time, but there will often be some more investigation to do first to get the correct YANG module path, compared to your well-known CLI command to do the same

The example will:

* Get all interfaces from the IOS-XE device using RESTCONF, including the descriptions
* If the description of GigabitEthernet1 contains the word "Uplink" it will do nothing
* If the description of GigabitEthernet1 does NOT contain the word "Uplink", it will create a new text for the description, with "Uplink" and a timestamp for the change
* Push the updated interface config (description) back to the device using RESTCONF

{% hint style="info" %}
Be aware that this example takes a lot of shortcuts, just to show the concept. Like being valid only for GigabitEthernet1's description. And no error checking (try to run it if you have no description at all on the Gig1 interface…)
{% endhint %}
