Title: Instalace HP Data Protector DA na CentOS
X-Modified: 2015-01-18 22:00
Category: External memory
Tags: hp-data-protector
Authors: Věroš Kaplan
Summary: Step-by-step instalace nainstalovat HP Data Protector na CentOS 6.
Slug: hp-data-protector-centos
Language: czech
X-Status: testing

Kdysi dávno jsem dokázal nainstalovat Disk Agent od HP Omniback na Linux, čímž jsem si 
v jedné továrně získal nehynoucí obdiv místních IT techniků. Čas od času
za tento hřích mládí musím zaplatit, protože mi volají lidé, že chtějí 
CentOS zálohovat pomocí HP Data Protector a chtějí tam nainstalovat jeho Disk Agent.

Jak na to?

1. Sehnat médium HP Data protectoru. 

2. Data protector běží jako služba v inetd (a dokonce umí i xinetd). 
  *Před* instalací je  třeba nainstalovat inetd nebo xinetd.

        :::bash
        yum install xinetd -y

3. Data Protector chce mít pocit, že na portu 5555 nic neběží a ověřuje si to 
   velmi humorným způsobem. Z `/etc/services` smažeme řádek obsahující 5555

        :::bash
        sed -i~ /5555/d  /etc/services
     
     
4. Nainstalovat RPM balíčky Data Protectoru. Pokud to při instalaci nenapíše, tak je to 
    možná v pořádku. Pokud to napíše něco ošklivého, tak to v pořádku není.   

        :::bash
        rpm -ihv OB2-CORE-A.06.11-1.x86_64.rpm
        rpm -ihv OB2-DA-A.06.11-1.x86_64.rpm
    

5. *Přidat podpora moderních* (nebo obskurních) *filesystémů*. Pokud je HP DP DA velmi starý (~2011),
    tak nepodporuje například ext4. Pro jeho podporu je potřeba buď z HP sehnat patch
    (a tedy mít produkt pod supportem), nebo ohackovat klienta.

    Editovat skript /opt/omni/lbin/.util , najít řádek 351 a do řádku přidat **-t ext4** 
    nejlépe hned za **-t ext3** .

        ::::bash
        gpl/i386/linux)
             /bin/df -P -t psfs -t ext2 -t SFS -t ext -t minix -t xiafs -t vmfs -t reiserfs -t ext3 -t ext4 -t vfat -t vxfs -t xfs -t hsmfs -t gfs -t lustre_lite -t ocfs -t ocfs2 2>/dev/null | sed '1d' | awk '{print $6}'
       



**DISCLAIMER:** Tohle jsou poznámky jak jsem něco udělal, abych na to nezapomněl.
 
Novým zákazníkům bych doporučil [Bareos] (který nasazuju). Pokud ale někdo má legacy
system s HP dlouhé peníze, nedá se nic dělat...

[Bareos]: http://www.bareos.org/
