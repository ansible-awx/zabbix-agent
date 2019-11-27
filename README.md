* This awx ansible runbook was adapated from R1 to install the zabbix agents in Linux.

* This cookbook installs the zabbix agent version 4.4, but can be modified to install any agent version (Tweaks required in tasks/install.yml)

* The related rpms must be placed in rpms folder

* The hosts in which this should be installed should be added to "hosts" file

* The ansible playbook command that I use is below,

```
	* ansible-playbook -v -i /path/tothe/folder/hosts -k -K install.yml --extra-vars "user=<username>"
	* ansible-playbook -v -i /path/tothe/folder/hosts -k -K uninstall.yml --extra-vars "user=<username>"
```

* Use either one of the yml file depending on if you are going to install the agent in stage or prod.

* ansible-awx Playbook layout

```
[me@awx01 zabbix-agent]$ tree .
.
├── hosts
├── install.yml
├── README.md
├── rpms
│   └── zabbix-release-4.4-1.el7.noarch.rpm
├── tasks
│   ├── remove.yml
│   └── zabbix_install_v4.yml
├── templates
│   ├── zabbix_agentd.conf
│   └── zabbix_sudoers
├── uninstall.yml
└── vars
    └── zabbix_main.yml

4 directories, 16 files
[me@awx01 zabbix-agent]$ 
```

* Reference: 
  * R1: https://github.com/hvaithia/Ansible-zabbix-agent-installation