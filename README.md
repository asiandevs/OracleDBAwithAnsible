# OracleDBAwithAnsible SI (Single Instances)

Note: Please modify all necessary configuration files based on your own environment.

This article describes the installation of Oracle Database 19c 64-bit on Oracle Linux 7 (OL7) 64-bit.

Oracle Installation Prerequisites: Database Installation Guide for Linux 
(https://docs.oracle.com/en/database/oracle/oracle-database/19/ladbi/index.html)

**Setup:**
 * OS: OEL 7.5 
 * Ansible: ansible 2.7.6
 * Database Version: Oracle 19.3 Linux64

Oracle RDBMS Software:
> Download the Oracle software from OTN or MOS depending on your support status. 
> Oracle binaries are staged from the "edelivery: Oracle Database 19c Software (64-bit)".
> They have to be manually downloaded and made available for this article to apply. 


- Install Oracle Database Software
Oracle DBA - Automation with Ansible (Install Oracle 19c Database Software)

### Summary Steps:  
 * 1  :Stage Oracle 19c RDBMS software from edelivery.oracle.com. 
 * 2  :Unpack Oracle 19c RDBMS Software
 * 3  :Install Oracle 19c RDBMS Software
 * 4  :Execute oraInstroot.sh script
 * 5  :Execute root.sh script
 * 6  :Validation - Connect to SQLPLUS binary. 

### Summary commands: 

1. Clone this repository:
   git clone https://github.com/asiandevs/OracleDBAwithAnsible

2. Stage the following Oracle Software on the control machine
> Oracle Database 19c (19.3) for Linux x86-64 [ LINUX.X64_193000_db_home.zip ]
> https://www.oracle.com/technetwork/database/enterprise-edition/downloads/oracle19c-linux-5462157.html

3. Configure an Ansible inventory file (example as below) 

```
[root@oel75 ansible]# cat ansible.cfg | grep inventory
inventory = ./inventory
[root@oel75 ansible]# cat inventory
[ora-x1]
192.168.56.102
[ora-x2]
192.168.56.103
[dbservers]
192.168.56.102
192.168.56.103
```

4. Run the playbook role `dbsoftware19c_install`
```
ansible-playbook dbsoftware19c_install  [ with options for testing, use --check / --diff / --step / -vvv ]
```

You can use:
Mode         | Option for
------------ | -------------
--check      | Check mode is just a simulation
--diff       | reports the changes made
--step       | ansible to stop on each task, and ask if it should execute that task.
-v           | verbose mode (-vvv for more, -vvvv to enable connection debugging)

[Ansible](https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html)
