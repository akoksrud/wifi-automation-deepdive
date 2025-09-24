# 205. Python modules

If you want to do some stuff that is not supported in the builtin or community modules, you can write your own module. It can be small or large project, but it can also be something that is simple in Python, but that you would need to make complex structures in Ansible to solve

The example will

* Get "show run" from our device(s) using the cisco.ios.ios\_facts module
* Call our own module that use the input and return values based on that
* Print the result

This is a simple test/demo of a module. Some practical use of this module could be to check whether RESTCONF is enabled on a device, and based on the result of this test you could run other tasks as either RESTCONF, or fallback to CLI mode if RESTCONF is not available.
