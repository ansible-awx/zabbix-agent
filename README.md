* This ansible runbook was created to install the zabbix agents in Linux

* I have 2 yml files to use for installation of the agents in stage and prod environments (The std we follow in our company)
* This cookbook installs the zabbix agent version 2.2.2, but can be modified to install any agent version (Tweaks required in tasks/zabbix_install_v2_2_2.yml)
#The related rpms must be placed in rpms folder
#The hosts in which this should be installed should be added to "hosts" file
#The ansible playbook command that I use is below,
	#ansible-playbook -v -i /path/tothe/folder/hosts -k -K zabbixhostsprod.yml --extra-vars "user=<username>"
	#ansible-playbook -v -i /path/tothe/folder/hosts -k -K zabbixhostsstage.yml --extra-vars "user=<username>"
#Use either one of the yml file depending on if you are going to install the agent in stage or prod.
#You can also create a single yml file if you do not require the stage/prod distinction


* layout
```
[me@awx01 zabbix-agent]$ tree .
.
├── hosts
├── install.yml
├── README.md
├── rpms
│   ├── zabbix-2.2.2-1.el6.x86_64.rpm
│   ├── zabbix-agent-2.2.2-1.el6.x86_64.rpm
│   └── zabbix-release-4.4-1.el7.noarch.rpm
├── tasks
│   ├── remove.yml
│   ├── zabbix_install_v2_2_2.yml
│   └── zabbix_install_v4.yml
├── templates
│   ├── zabbix_agentd.bash.old
│   ├── zabbix_agentd.conf
│   ├── zabbix_agentd.conf.old
│   ├── zabbix_agentd_linux_old
│   └── zabbix_sudoers
├── uninstall.yml
└── vars
    └── zabbix_main.yml

4 directories, 16 files
[me@awx01 zabbix-agent]$ 
```

* Reference: 
  