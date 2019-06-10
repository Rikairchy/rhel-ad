RHEL-AD
=========

This role installs the required packages on a RedHat machine to join a Microsoft Active Directory domain, including using the sshPublicKeys attribute in AD to permit storing SSH public keys in Active Directory

Requirements
------------

easy_install - this role will use easy_install to install Pip. Pip is not installed by default on RHEL7

Role Variables
--------------

|Variable Name|Description|Example|Required|
|---|---|---|---|
|packages|list of software required to join AD|See defaults/|No|
|ad_user|Username to join AD|first.last|Yes|
|ad_pass|Password to join AD|password1|Yes|
|linux_ou|DN of the OU to join|OU=Linux,DC=domain,DC=tld|Yes|
|domain_name|Domain name to join|domain.tld|Yes|


Dependencies
------------

None

Example Playbook
----------------

```
- hosts: ALL
  tasks:
  - name: Join to AD
	import_role:
	  name: Linux-AD-Join
	vars:
	  ad_user: "{{ first.last.admin }}"
	  ad_pass: "{{ hostvars.localhost.ad_pass }}"
	  linux_ou: "{{ OU=Linux,DC=domain,DC=tld }}"
	  domain_name: "{{ domain.tld }}"

```

License
-------

BSD

Author Information
------------------

https://github.com/rikairchy
