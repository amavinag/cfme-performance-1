- [Configure](#configure)
  - [sshkey.yml](#sshkey.yml)
  - [hostname.yml](#hostname.yml)
  - [repos.yml](#repos.yml)
  - [chronyd.yml](#chronyd.yml)
  - [config-interface.yml](#config-interface.yml)
  - [proctitle-patch.yml](#proctitle-patch.yml)
  - [init-vmdb.yml](#init-vmdb.yml)
  - [collectd.yml](#collectd.yml)

# Configure

Playbooks that configure an appliance for Performance Analysis and Testing.

## sshkey.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/sshkey.yml
```
Installs the current user's ssh key into the appliances root user's authorized_key file therefore enabling all other playbooks to run.  After running this playbook you can change the default CFME/Miq appliance password to something secure.

## hostname.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/hostname.yml
```
Sets the appliances hostname to the ansible inventory name.  To produce the intended affect, you should map each inventory file mapping to a host entry in your ~/.ssh/config file.

## repos.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/repos.yml
```
Installs a cfme-performance.repo file into /etc/yum.repos.d directory with necessary repos to install cfme-performance tooling.

## chronyd.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/chronyd.yml
```
Installs and configures chronyd service to ensure time is synchronized.

## config-interface.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/config-interface.yml
```
(Optional) Configures second interface on CFME/Miq appliances with a static address.

## proctitle-patch.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/proctitle-patch.yml
```
(CFME 5.5.x appliances only) Applies patch to CFME 5.5.x appliances to show process title for ruby workers.

## init-vmdb.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/init-vmdb.yml
```
(CFME VMDB appliances only) Installs the dev v2_key and initializes the Postgres database for the region configured in ../group_vars/all.yml (or overriden by all.local.yml) on cfme-vmdb appliances.

## collectd.yml
```
[root@perf ansible]# ansible-playbook -i hosts.local configure/collectd.yml
```
Installs and configures collectd on CFME/Miq appliances.