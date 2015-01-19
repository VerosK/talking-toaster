Title: Owncloud 7 - upgrade from 6
Modified: 2015-01-15 22:00
Category: External memory
Tags: owncloud
Authors: Věroš Kaplan
Summary: Quick upgrade from OwnCloud 6 to OwnCloud 7
X-Status: testing

[OwnCloud 7][owncloud7] is here for more than three months ([changelog][owncloud-changelog]). How to upgrade from
OwnCloud 6?

The good news: it's easy.

* Make backups
* [Download][owncloud-download] .tar.gz package and extract it
* Copy `owncloud6/config/config.php` to `owncloud7/config/config.pjp`
* Run migration tasks by: ` sudo -u apache php occ upgrade`

[owncloud7]: http://www.owncloud.com/seven/
[owncloud-download]: https://owncloud.org/install/#instructions-server
[owncloud-changelog]: https://owncloud.org/releases/Changelog
