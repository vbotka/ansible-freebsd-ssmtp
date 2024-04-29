# freebsd_ssmtp

[![quality](https://img.shields.io/ansible/quality/27910)](https://galaxy.ansible.com/vbotka/freebsd_ssmtp)[![Build Status](https://app.travis-ci.com/vbotka/ansible-freebsd-ssmtp.svg?branch=master)](https://app.travis-ci.com/vbotka/ansible-freebsd-ssmtp)[![GitHub tag](https://img.shields.io/github/v/tag/vbotka/ansible-freebsd-ssmtp)](https://github.com/vbotka/ansible-freebsd-ssmtp/tags)

[Ansible role.](https://galaxy.ansible.com/vbotka/freebsd_ssmtp/) FreeBSD. Install and configure SSMTP.

Feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-freebsd-ssmtp/issues).

[Contributions are welcome](https://github.com/firstcontributions/first-contributions).


## Requirements

### Packages

* FreeBSD package or port mail/ssmtp

### Collections

* community.general


## Variables

Review the defaults and examples in vars.


## Workflow

1) Change shell on the remote host to /bin/sh if necessary

```
shell> ansible mailserver -e 'ansible_shell_type=csh ansible_shell_executable=/bin/csh' -a 'sudo pw usermod freebsd -s /bin/sh'
```

2) Install the role and collections

```bash
shell> ansible-galaxy role install vbotka.freebsd_ssmtp
```

Install the collection if necessary

```bash
shell> ansible-galaxy collection install community.general
```

3) Fit variables


4) Create playbook and inventory

```bash
shell> cat freebsd_ssmtp.yml

- hosts: mailserver
  roles:
    - vbotka.freebsd_ssmtp
```

```bash
shell> cat hosts
[mailserver]
<mailserver-ip-or-fqdn>
[mailserver:vars]
ansible_connection=ssh
ansible_user=freebsd
ansible_become=true
ansible_become_method=sudo
ansible_python_interpreter=/usr/local/bin/python3.9
ansible_perl_interpreter=/usr/local/bin/perl
```

5) Install and configure the mailserver

```bash
shell> ansible-playbook freebsd_ssmtp.yml
```

6) Test it

```bash
shell> echo -n 'Subject: test\n\nTesting ssmtp' | sendmail -v admin@example.com
```


## Ansible lint

Use the configuration file *.ansible-lint.local* when running
*ansible-lint*. Some rules might be disabled and some warnings might
be ignored. See the notes in the configuration file.

```bash
shell> ansible-lint -c .ansible-lint.local
```


## References

- [FreeBSD handbook: Setting Up to Send Only](https://docs.freebsd.org/en/books/handbook/mail/#outgoing-only)
- [FreeBSD handbook: Changing the Mail Transfer Agent](https://docs.freebsd.org/en/books/handbook/mail/#mail-changingmta)
- [ArchLinux SSMTP](https://wiki.archlinux.org/index.php/SSMTP)


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.info)
