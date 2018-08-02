# Ansible Role: windows.java

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
This role assumes that there is a central repository where the downloaded packages of the latest versions are present. Below is the folder structure:

`\\your_repository_name\jdk\jdk8_181_64.exe` and `\\your_repository_name\jdk\jdk8_181_32.exe`

`\\your_repository_name\jre\jre-8u181-windows-x64.msi` and `\\your_repository_name\jre\jre-8u181-windows-i586.msi`

Make sure to replace all occurences of "your_repository_name" with the server name or ip address of the windows share inside the tasks/main.yml

Role Variables
--------------
*jdk/jre packages will be copied to target machines under the stage directory*
	
	---
	stage: C:\temp

*complete path of packages on the target machines after they have been copied*

	---
	_64_jdk_package_path: C:\temp\jdk\jdk8_181_64.exe
	_32_jdk_package_path: C:\temp\jdk\jdk8_181_32.exe
	_64_jre_package_path: C:\temp\jre\jre-8u181-windows-x64.msi
	_32_jre_package_path: C:\temp\jre\jre-8u181-windows-i586.msi

*used for creates_path. This allows installation of packages without knowing the product_id*

	---
	_64jdk: C:\Program Files\Java\jdk
	_64jre: C:\Program Files\Java\jre
	_32jdk: C:\Program Files (x86)\Java\jdk
	_32jre: C:\Program Files (x86)\Java\jre


Dependencies
------------
None

Example Playbook
----------------

*Uninstall all versions of Java and upgrade those versions to the latest*

        ---
        - hosts: servers
          roles:
            - role: rishihegde.windows.java

*Use tags to only install specific versions or only uninstall*

        ---
        - hosts: servers
          roles:
            - { role: rishihegde.windows.java, tags: ['uninstall'] }

        ---
        - hosts: servers
          roles:
            - { role: rishihegde.windows.java, tags: ['uninstall','64_jdk'] }


*Available tags*
1. uninstall - only uninstalls all versions of jre/jdk that currently exists on the target machine
2. jdk_both - only installs 64bit and 32bit version of JDK
3. 64_jdk - only installs 64bit JDK
4. 32_jdk - only installs 32bit JDK
5. 64_jre - only installs 64bit JRE
6. 32_jre - only installs 32bit JRE

License
-------

BSD

Author Information
------------------
Rishi Hegde	rishihegde810@gmail.com
