Title: Instalace HP Data Protector DA na CentOS
X-Modified: 2015-01-18 22:00
Category: External memory
Tags: hp-data-protector
Authors: Věroš Kaplan
Summary: Step-by-step instalace nainstalovat HP Data Protector na CentOS 6.
Slug: owncloud-share-by-mail
X-Status: testing

Musí být instalovaný inetd nebo xinetd.

```bash
yum install xinetd -y
```
Z `/etc/services` smazat řádek 5555

```bash
sed -i~ /5555/d  /etc/services
 ```
 
Nainstalovat balíčky Data Protectoru.

```bash
rpm -ihv OB2-CORE-A.06.11-1.x86_64.rpm
rpm -ihv OB2-DA-A.06.11-1.x86_64.rpm
```

Osobně bych dal přednost Bareosu, ale když už někdo zaplatil HP dlouhé peníze, tak co s ním... 


