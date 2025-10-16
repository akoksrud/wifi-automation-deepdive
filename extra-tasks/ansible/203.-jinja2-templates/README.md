---
icon: triangle-exclamation
---

# 203. Jinja2 templates

<mark style="color:yellow;">(There is an error in this exercise, so please see through the examples, but do not expect it to actually work. I will troubleshoot and/or correct this task or replace it with a working task when I have time)</mark>

Jinja2 is a templating language, widely used by developers to create text files that have placeholders, which can be filled inn with various values. One very common example is HTML

Jinja2 is a native part of Ansible and the YAML files there. So anytime you write something in double curly braces it is a Jinja2 variable that will be replaced by the content of the variable when you run the playbook

Instead of using Jinja2 inline, we can store templates as separate files, and then refer to those templates when running our playbook

In this exercise, we will modify the playbook from our CLI configuration exercise to use Jinja2 templates instead of spelling out the commands in the playbook itself

One advantage of using templates is to reuse a playbook for various templates

Another advantage is the possibility to loop in the template itself, for instance looping over all site tags
