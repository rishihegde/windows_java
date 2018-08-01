javaupgrade
=========

Ansible role to upgrade JRE/JDK to latest version. Tasks in this role will do the following.

1. Log information about existing versions of Java (jre/jdk) under C:\JavaPreviousVersions.txt
2. Uninstall all existing versions of Java (jre/jdk) from the target machine
3. Ugrade to the latest version of Java (jre/jdk)
4. Upgrade will maintan bit versions which means if 32 bit version was previously present, the latest version being installed will also be 32bit and likewise for 64bit.
5. The above default feature can be overridden by tags that have provided.
6. Whichever component of Java (jre/jdk) was previously present on the machine will be upgraded.
7. Cleanup packages that were copied to the target machine.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

*Uninstall all versions of Java and upgrade those versions to the latest*
- hosts: servers
  roles:
    - role: rishihegde.javaupgrade 

*Use tags to only install specific versions or only uninstall*
- hosts: servers
  roles:
    - { role: rishihegde.javaupgrade, tags: ['uninstall'] }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
