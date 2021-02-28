toni.keycloak
===========

Ansible role to install Keycloak with standard realm (Nginx) used by toni.openresty role (authenticating proxy/(SSO))
The Nginx realm is preconfigured and gets imported during installation.
User "jidu" is created. After installation the password has to be changed.

todo: Use Keycloak api to setup realm instead of importing an "existing one", extend documentation.

License
-------

MIT

Author Information
------------------

T.Nissen