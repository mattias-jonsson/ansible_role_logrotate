Ansible Role: ansible_role_logrotate
=========

Installs and configures logrotate on the following Linux distributions:

<ul>
<li>Red Hat Enterprise Linux 7
<li>Red Hat Enterprise Linux 8
</ul>


Requirements
---------------

None.

Role Variables
--------------

| Variable | Required | Default | Comments |
| -------- | -------- | ------- | -------- |
| `name` | Yes | | Name of logrotate configurationfile. |
| `paths` | Yes | [] | List of files to rotate |
| `options` | Yes | [] | List of rotation options, see logrotate man page for availbale options. |
| `postrotate_scripts` | Yes | [] | List of scripts to run after rotation |
| `prerotate_scripts` | Yes | [] | List of scripts to run before rotation |


Dependencies
------------

None.


Example Playbook
----------------


    - hosts: servers

      vars:
        ansible_role_logrotate_options:
          - name: testfile_1.conf
            paths:
              - /var/log/testfile1
            options:
              - daily
              - compress
            postrotate_scripts:
              - /script/ett.sh
            prerotate_scripts:
              - /scripts/tva.sh
          - name: testfile_2.conf
            paths:
              - /var/log/testfile2
            options:
              - daily
              - compress
            postrotate_scripts:
              - /script/ett.sh
            prerotate_scripts:
              - /scripts/tva.sh

      roles:
         - ansible_role_logrotate

License
-------

MIT

Author Information
------------------

Mattias Jonsson
