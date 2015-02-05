Title: Migrate Redmine internal users to LDAP
X-Modified: 2015-01-15 22:00
Category: External memory
Tags: redmine, ldap
Authors: Věroš Kaplan
Summary: Notes on migrating Redmine users to LDAP
X-Status: testing

[Redmine][redmine] can authenticate it's users to multiple backends. 

What if you need to change you internal users to LDAP ones?  

* Create new *LDAP backend* in Administration ( It's in http://my.redmine.org/auth_sources )
    * Add new `Auth source* and *Test* it. It should return no users, it's OK.
* Change one or two users to authenticate to new LDAP auth source. (I'ts in https://my.redmine.org/users/1/edit ) 
* Check that these users can login
* Change all other users. 
    * You can eventually use ` UPDATE users SET auth_source_id = NEW_ID WHERE auth_source_id = OLD_ID`
* Enjoy.

## How to make backups of auth setup

` mysqldump  redmine_database users --replace --extended-insert=FALSE --no-create-info > redmine_users.sql `
```

[redmine]: http://www.redmine.org/
