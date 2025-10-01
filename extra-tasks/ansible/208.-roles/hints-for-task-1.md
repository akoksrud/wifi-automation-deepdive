# Hints for Task 1

We start with creating the `audit-network-playbook.yml` content

It consists of two tasks, as you can see there is not any explicit "doing" in these tasks, they just have some roles assigned

To expand this example, you could have more roles under the relevant tasks for the different device groups. For instance, the roles under the first task could also include roles "get\_restconf\_status", "backup\_run\_config" etc. The WLC specific task could have roles for "get\_ap\_summary", "get\_wireless\_clients" etc

Our reusable roles are entered under the "roles" section in each task

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1).png" alt="" width="506"><figcaption></figcaption></figure>
