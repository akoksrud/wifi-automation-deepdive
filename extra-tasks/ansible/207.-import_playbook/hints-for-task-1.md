# Hints for Task 1

To accommodate for more than only WLCs, we create a slightly more advanced structure for our inventory file than we have done until now

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt="" width="440"><figcaption></figcaption></figure>

1. Top-level group is <kbd>all</kbd>
2. Under <kbd>all</kbd> we have sub-group <kbd>children</kbd>
3. Under <kbd>children</kbd> we have two groups, <kbd>wlc</kbd> and <kbd>switch</kbd>
4. The <kbd>vars</kbd> in this example are common for all devices, so we have it directly under the <kbd>all</kbd> group, on the same level as <kbd>children</kbd>. It is also possible to have "vars" under each child group (on the same level as "hosts"), or under each host. None of those are used in this example.



