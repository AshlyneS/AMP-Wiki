AMP supports authenticating users via LDAP to provide centralised authentication either across different AMP systems or other applications. This also allows you to authenticate against any LDAP compatible domain controller such as Active Directory.

LDAP authentication in AMP requires a Network Edition or higher-tier licence (this feature is not available in AMP Professional).

AMP uses group membership within the directory to determine which AMP roles a user belongs to. AMP allows you to specify a prefix for groups to allow you to separate AMP groups from anything else on your network. E.g. A user in the "AMP_Users" group with the prefix being "AMP_" would match up with a role in AMP called "Users".

# Setting up for the first time

## Creating a role

Before you start, you need to sign into AMP normally - and create a new role for AMP administrators. Having done this you must then shut down AMP to alter its configuration.

## Editing the configuration

In AMPConfig.conf for your ADS instance, under the Login section you'll see the following settings:

```
Login.UseLDAPLogins=False
Login.LDAPAuthDomain=
Login.LDAPGroupPrefix=AMP_
```

Set `UseLDAPLogins` to `True` and set the `LDAPAuthDomain` to the name of the domain to authenticate against. If you want to use a different prefix for your directory groups then you can change it here (or remove the prefix entirely to match group names -> roles verbatim)

## Creating your directory user and groups

If in AMP we've named our new role created above "Admins" with a prefix of "AMP_" then in our directory server we should create a group called "AMP_Admins" and assign any users to it. This follows for any other roles that you wish to be able to use within AMP.

# Implementation Notes

 * When using LDAP, Usernames are case-insensitive. Normally AMP logins are case-sensitive. AMP will query the correct casing of the supplied username from the LDAP server and use it internally.
 * When a user logs in via LDAP for the first time, AMP will internally create a matching user (it does not store their password) to match against the directory user. This allows AMP to store user information such as their email address, and any authentication tokens to allow the 'Remember Me' functionality to work.
 * Deleting the LDAP user in AMP wipes this information - but the user will be re-created if the user logs in again. When deleting users you should first remove them from your directory server before removing them from AMP.