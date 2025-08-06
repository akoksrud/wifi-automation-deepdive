# Intro

* In this exercise, we will write a playbook that does some CLI configuration
* A key concept of Ansible is "idempotency". That basically means
  * If something IT NOT configured, then go ahead and configure it
  * If something IS configured, just skip the task.
  * That means: DO NOT configure the same stuff again if it isn't necessary
* This exercise will create a task that does this for a small part of the configuration. It can of course be expanded to a complete config. There are many ways to do this, some of which are
  * Putting everything in a gigantic playbook with hundreds of tasks (it might get heavy to navigate)
  * Splitting tasks for small config snippets in separate files, and call them all from a "master playbook"
  * Using Jinja2 templates (we will try this in a later exercise)
  * Using Ansible roles in combination with templates or tasks
  * ... and many many more ;-)
