# Example solution

Here is an example solution:

```yaml
---
- name: CLI configuration
  hosts: wlc
  connection: network_cli
  gather_facts: false

  tasks:

    - name: "Configure policy profile: clients_policy_profile"
      cisco.ios.ios_config:
        before:
          - wireless profile policy clients_policy_profile
          - shutdown
        lines:
          - idle-timeout 3000
          - passive-client
          - session-timeout 43200
          - vlan 11
        after:
          - no shutdown
        parents: wireless profile policy clients_policy_profile

```

First time run, output should be like this:

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure></div>

And the policy profile should appear on the WLC:

<figure><img src="../../../.gitbook/assets/image (2).png" alt="" width="392"><figcaption></figcaption></figure>

On next run, config should already be present, and "changes" will be 0:

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure></div>
