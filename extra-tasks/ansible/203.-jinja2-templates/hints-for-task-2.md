# Hints for Task 2

Now we will try changing some of the static config in the template with some parameters. The parameters can come from different sources:

* hosts.yml (will be used in this exercise)
* Specific directories like <kbd>group\_vars/</kbd> and <kbd>host\_vars/</kbd>
* External systems using APIs (NetBox, Catalyst Center, etc)

Let us modify our files:

* <kbd>hosts.yml</kbd>
  *   In the bottom of this file, create a list with three items, each of them containing a

      * Policy profile name ("name")
      * VLAN for the policy profile ("vlan")

      <div align="left"><figure><img src="../../../.gitbook/assets/image (180).png" alt="" width="323"><figcaption></figcaption></figure></div>
* <kbd>jinja2-playbook.yml</kbd>
  * Use the "loop" statement in the playbook, to loop over the policy\_profiles list you created
  * To reference the items that you loop over, you use keyword "item"
  *   To reference sub-values, use dot notation or square bracket notation

      * In the example below, we use both methods. Both are perfectly fine

      <div align="left"><figure><img src="../../../.gitbook/assets/image (181).png" alt="" width="539"><figcaption></figcaption></figure></div>
*   <kbd>policy\_profile\_template.j2</kbd>

    * Use the notation in the .j2 template as well

    <div align="left"><figure><img src="../../../.gitbook/assets/image (183).png" alt="" width="377"><figcaption></figcaption></figure></div>
