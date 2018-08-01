Ansible role to upgrade JRE/JDK to latest version. Tasks in this role will do the following.

1. Log information about existing versions of Java (jre/jdk) under C:\JavaPreviousVersions.txt
2. Uninstall all existing versions of Java (jre/jdk) from the target machine
3. Ugrade to the latest version of Java (jre/jdk)
  ...a. Upgrade will maintan bit versions which means if 32 bit version was previously present, the latest version being installed will also be 32bit and likewise for 64bit.
  ...b. The above default feature can be overridden by tags that have provided.
  ...c. Whichever component of Java (jre/jdk) was previously present on the machine will be upgraded.
