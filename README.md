Minimalistic nagios setup playbook for ansible
==============================================

Installs nagios server on nagios host and nagios nrpe on nagios clients.
Based on CentOS 7.2 distro.


1. Update inventory file and vars in group_vars files and run the playbook
---

```
ansible-playbook -i example-inventory.ini example-install-nagios.yml --tags "config"                                           
```

2. To regenerate configs run the playbook with --tags option
---

```
ansible-playbook -i example-inventory.ini example-install-nagios.yml --tags "config"                                           
```

3. By default this playbook generates in /etc/nagios/conf.d/: 
---

```
hosts.cfg                                                                                                                      
hostgroups.cfg                                                                                                                 
service-ping-ssh.cfg                                                                                                           
service-custom-http.cfg                                                                                                        
service-nrpe-common.cfg                                                                                                        
```

See `tasks/main.yml` for more details.

Add more service configs to the `templates/` directory and update tasks/main.yml file.

Use example with dictionaries in `group_vars/web.yml` and jinja templates in `templates/service-custom-http.cfg.j2`.
