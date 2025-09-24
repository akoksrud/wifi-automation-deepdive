# Hints for Task 2

Here are some tips for writing the Ansible playbook:

* To perform the RESTCONF call, use the module "ansible.builtin.uri". Check the Ansible documentation for how-to and examples
* "url" should be copy-paste of what you have tested in Postman, just replace \{{host\}} with \{{ ansible\_host\}}
* Try to replicate headers, body format and method from Postman
* Do not validate certs
* Specify some valid HTTP status codes, at least status code 200
* Create a second task for printing the results. Start by printing all of the result.
* Try to narrow down the printing (think, what can you do with the results beside printing to the screen. It might be out of scope for this lab, but very nice to test how you can manipulate the results). Tips, the following is the first step

```yaml
    - name: "View result"
      ansible.builtin.debug:
        msg: {{result['json']}}
      when: result.status == 200
```

* Use a when: statement on the print results part. It should only run when the status code is 200 "OK".

