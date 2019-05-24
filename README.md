Example of Networking Inventory with Ansible
============================================

One of the many use cases for Ansible and the [networking modules][2] is to grab
information in real time from the network.  In this example I will generate a
HTML report using the template module from facts I have gathered with the
[nxos_facts module][1].  ![HTML report generated by template module][3]


Running the playbook
--------------------

Use the `ansible-playbook` command:
```
[root@localhost ansible_inventory_report]# ansible-playbook inventory.yml

PLAY [cisco] ******************************************************************

TASK [gathering nxos facts] ***************************************************
ok: [n9k3]
ok: [n9k4]
ok: [n9k5]
ok: [n9k2]
ok: [n9k]
ok: [n9k6]

TASK [create HTML report] *****************************************************
changed: [n9k -> localhost]

PLAY RECAP ********************************************************************
n9k                        : ok=2    changed=1    unreachable=0    failed=0
n9k2                       : ok=1    changed=0    unreachable=0    failed=0
n9k3                       : ok=1    changed=0    unreachable=0    failed=0
n9k4                       : ok=1    changed=0    unreachable=0    failed=0
n9k5                       : ok=1    changed=0    unreachable=0    failed=0
n9k6                       : ok=1    changed=0    unreachable=0    failed=0
```

A very similar playbook can be used to generate a report for Cisco IOS devices
using the [ios_facts module][4]

```
[root@localhost ansible_inventory_report]# ansible-playbook inventory-ios.yml

PLAY [build IOS XE inventory] *************************************************

TASK [gathering IOS XE facts] *************************************************
ok: [172.26.249.162]
ok: [172.26.249.161]
ok: [172.26.249.164]
ok: [172.26.249.163]
ok: [172.26.249.160]
ok: [172.26.249.151]
ok: [172.26.249.166]
ok: [172.26.249.153]
ok: [172.26.249.169]
ok: [172.26.249.152]
ok: [172.26.249.154]
ok: [172.26.249.159]

TASK [create HTML report] ***************************************************
changed: [172.26.249.160 -> localhost]

PLAY RECAP ******************************************************************
172.26.249.151             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.152             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.153             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.154             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.159             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.160             : ok=2    changed=1    unreachable=0    failed=0
172.26.249.161             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.162             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.163             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.164             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.166             : ok=1    changed=0    unreachable=0    failed=0
172.26.249.169             : ok=1    changed=0    unreachable=0    failed=0
```

---
![Red Hat Ansible Automation][6]

Red Hat® Ansible® Automation consists of  three products:

- [Red Hat® Ansible® Tower][7]: Built for operationalizing and scaling
  automation, managing complex deployments and speeding up productivity. Extend
  the power of Ansible Tower with Workflows and Surveys to streamline jobs and
  simple tools to share solutions with your team.

- [Red Hat® Ansible® Engine][8]: a fully supported product built on the
  foundational capabilities of the Ansible project. Also provides support for
  select modules including Infoblox.

- [Red Hat® Ansible® Network Automation][9]: provides support for select
  networking modules from Arista (EOS), Cisco (IOS, IOS XR, NX-OS), Juniper
  (JunOS), Open vSwitch, and VyOS. Includes Ansible Tower, Ansible Engine, and
  curated content specifically for network use cases.

[1]: http://docs.ansible.com/ansible/latest/nxos_facts_module.html
[2]: http://docs.ansible.com/ansible/latest/list_of_network_modules.html
[3]: images/htmlreport.png
[4]: http://docs.ansible.com/ansible/latest/ios_facts_module.html
[5]: http://docs.ansible.com/ansible/latest/template_module.html
[6]: images/rh-ansible-automation.png
[7]: https://www.ansible.com/tower
[8]: https://www.ansible.com/ansible-engine
[9]: https://www.ansible.com/networking
