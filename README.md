freebsd_ssmtp
=============

[![Build Status](https://travis-ci.org/vbotka/ansible-freebsd-ssmtp.svg?branch=master)](https://travis-ci.org/vbotka/ansible-freebsd-ssmtp)

[Ansible role.](https://galaxy.ansible.com/vbotka/freebsd_ssmtp/) FreeBSD. Install and configure SSMTP.


Requirements
------------

No requiremenst.


Variables
---------

TBD. Review the defaults and examples in vars.


Workflow
--------

1) Change shell to /bin/sh.

```
# ansible mailserver -e 'ansible_shell_type=csh ansible_shell_executable=/bin/csh' -a 'sudo pw usermod freebsd -s /bin/sh'
```

2) Install role.

```
# ansible-galaxy install vbotka.freebsd_ssmtp
```

3) Fit variables.

```
# editor vbotka.freebsd_ssmtp/vars/main.yml
```

4) Create playbook and inventory.

```
# cat freebsd_ssmtp.yml

- hosts: mailserver
  roles:
    - vbotka.freebsd_ssmtp
```

```
# cat hosts
[mailserver]
<mailserver-ip-or-fqdn>
[mailserver:vars]
ansible_connection=ssh
ansible_user=freebsd
ansible_become=yes
ansible_become_method=sudo
ansible_python_interpreter=/usr/local/bin/python2.7
ansible_perl_interpreter=/usr/local/bin/perl
```

5) Install and configure the mailserver.

```
# ansible-playbook freebsd_ssmtp.yml
```

6) Test it

```
# echo -n 'Subject: test\n\nTesting ssmtp' | sendmail -v admin@example.com
```

License
-------

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


Author Information
------------------

[Vladimir Botka](https://botka.link)

References
----------

- [FreeBSD handbook: 28.7. Setting Up to Send Only](https://www.freebsd.org/doc/handbook/outgoing-only.html)
- [FreeBSD handbook: 28.4. Changing the Mail Transfer Agent](https://www.freebsd.org/doc/handbook/mail-changingmta.html)
- [ArchLinux SSMTP](https://wiki.archlinux.org/index.php/SSMTP)
