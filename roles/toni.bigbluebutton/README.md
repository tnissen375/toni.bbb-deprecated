toni.bigbluebutton
===========

Ansible role to Configure BBB.
This role has to be run after BBB Installation of BigBlueButton. 

Requirements
------------

Fully installed host. Have a look at bbb.yml in root dir.

Role Variables
--------------

```bash
# may be a little bit of duplication, cause i use this role without n0emis.bigbluebutton in my personal setup - does not harm.
- name: Configure BBB
  gather_facts: yes
  hosts: bigbluebutton
  handlers:
    - include: "/root/.ansible/roles/toni.openresty/handlers/main.yml"
  tasks:
  - name: Firewall BBB
    when: configure_firewall|bool
    include_role: { name: bigbluebutton, tasks_from: firewall }
  - name: Configure BBB SSL
    include_role: { name: bigbluebutton, tasks_from: ssl } 
  - name: Configure BBB Exporter
    when: configure_monitoring|bool
    include_role: { name: bigbluebutton, tasks_from: monitoring }
  - name: Configure BBB Privacy 
    include_role: { name: bigbluebutton, tasks_from: privacy }
```

Dependencies
------------
toni.openresty

License
-------

MIT

Author Information
------------------

T.Nissen
