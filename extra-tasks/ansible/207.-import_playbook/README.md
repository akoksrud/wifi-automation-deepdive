# 207. import\_playbook

For larger projects, there are several ways to organize stuff. A widely used concept is to break projects down into as small parts as possible, where each part will be easy to both maintain and understand. Good organization will make code easier to reuse, change and troubleshoot

We will explore two methods available in Ansible:

1. Run other playbooks from a playbook, by using the import\_playbook module, which we will do in this exercise
2. Call tasks by using the roles module, which is what we will do in the next exercise

General best practices (for Ansible and everything else…)

* Try to keep each part as simple as possible
* Use whitespace and comments to break things up and explain generously. What is obvious to you will probably not be obvious to everyone

In the following task we will create a (somewhat constructed) example using some of these techniques

Reference: [https://](https://docs.ansible.com/ansible/latest/tips_tricks/sample_setup.html)[docs.ansible.com](https://docs.ansible.com/ansible/latest/tips_tricks/sample_setup.html)[/ansible/latest/](https://docs.ansible.com/ansible/latest/tips_tricks/sample_setup.html)[tips\_tricks](https://docs.ansible.com/ansible/latest/tips_tricks/sample_setup.html)[/](https://docs.ansible.com/ansible/latest/tips_tricks/sample_setup.html)[sample\_setup.html#](https://docs.ansible.com/ansible/latest/tips_tricks/sample_setup.html)[sample-directory-layout](https://docs.ansible.com/ansible/latest/tips_tricks/sample_setup.html)
