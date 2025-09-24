# Example solution

### Explanation

<figure><img src="../../../.gitbook/assets/image (195).png" alt=""><figcaption></figcaption></figure>

1. Playbook and task header is similar to previous tasks
2. Using ansible.builtin.uri&#x20;
3. URL copy-paste from what is tested in Postman
4. Change host, user and password with the ansible\_host, ansible\_user and ansible\_password values
5. Try to replicate method, headers and body format from Postman
6. Do not validate the HTTPS certs (at least in this lab)
7. Valid return status codes
8. View the results using ansible.builtin.debug module
9. Only when the HTTP status code of the RESTCONF call is 200 ("OK")

### Example solution for copy-paste

{% code title="restconf-playbook.yml" %}
```yaml
---

- name: RESTCONF demo playbook
  hosts: wlc
  connection: network_cli
  gather_facts: false

  tasks:

    - name: "Get Certificate list with RESTCONF"
      ansible.builtin.uri:
        url: "https://{{ ansible_host }}/restconf/data/Cisco-IOS-XE-crypto-pki-oper:crypto-pki-oper-data/crypto-pki-bundle?fields=label;cert/subject-name;cert/validity-end"
        user: "{{ ansible_user }}"
        password: "{{ ansible_password }}"
        method: GET
        headers:
          Content-Type: 'application/yang-data+json'
          Accept: 'application/yang-data+json'
        body_format: json
        body:
        validate_certs: false
        status_code:
          - 200
          - 204
          - 404
      register: result

    - name: "View result"
      ansible.builtin.debug:
        msg: "{{ result['json']['Cisco-IOS-XE-crypto-pki-oper:crypto-pki-bundle'] }}"
      when: result.status == 200

```
{% endcode %}

### Example output

<figure><img src="../../../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>
