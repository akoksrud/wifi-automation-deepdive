# Hints for Task 2

This is the `audit-wlcs-playbook.yml`. The others in the example will be identical except the task name. For real-world the tasks for each device type would probably differ, else they don't need to be separate :relaxed:

We start with the usual playbook opening we have used in the previous tasks

<figure><img src="../../../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>

Then we have a "Gather IOS facts" task using the "cisco.ios.ios\_facts" module: Register the result in a variable for later use

<figure><img src="../../../.gitbook/assets/image (205).png" alt=""><figcaption></figcaption></figure>

Lastly we have a output task, using "ansible.builtin.debug" module to output parts of the registered results.

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure></div>

Notice we use Jinja2 here. To see the full contents of "facts1" you could run this using only `msg: {{ facts1 }}` to see what is contained within the results. Then expand to `msg: {{ facts1.ansible_facts }}` before using the single values in your text

Copy-paste this playbook to similar variants for router and switch (change `hosts: wlc` to `hosts: switch` and `hosts: router`)
