# phpldapadmin

Role installing and configuring phpldapadmin, a web interface for LDAP server management.

## Role Variables

- `phpldapadmin_dn`: DN of root of the tree managed by the LDAP server, e.g. dc=someproject,dc=fi. You must define this.
- `phpldapadmin_accounts_subtree`: subtree entry where your user accounts reside. Default is "ou=people".
- `phpldapadmin_ldap_uri`: URI of the LDAP server to manage, e.g. (and default) ldaps://127.0.0.1 if the LDAP server is installed on localhost
- `phpldapadmin_ldap_port`: port on which LDAP server listens, e.g. (and default) 636.
- `phpldapadmin_password_template`: template entry for inetOrgPerson password. Keep it to default.
- `phpldapadmin_binder_dn`: Account under which to bind to LDAP. Anonymous bind is not supported.
- `phpldapadmin_binder_password`: password for binder account

## Dependencies

It is beneficial to install a LDAP server from another Ansible role, best from https://git.forgeservicelab.fi/ansible-roles/openldap_server.git


## Example

```
   - role: phpldapadmin
     phpldapadmin_dn: "dc=forgeservicelab,dc=fi"
     phpldapadmin_binder_dn: "cn=binder,ou=people,dc=forgeservicelab,dc=fi"
     phpldapadmin_binder_password: "{{ binder_password }}"
```
