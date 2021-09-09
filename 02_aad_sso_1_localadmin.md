# Configure SAML Single Sign On (SSO) with Azure Active Directory (AAD) - Part 1

## Create a local (non-SSO) admin account for recovery

Navigate to the create account page in a private browser window and create an account.

```
https://<TFE HOSTNAME>/signup/account
```

![](screenshots/23.png?raw=true)

---

## Grant the local admin user administrative rights.

With the existing admin account, grant the local admin account admin rights.

![](screenshots/20.png?raw=true)

![](screenshots/24.png?raw=true)

![](screenshots/25.png?raw=true)

---

## Reference

* [SAML Single Sign On](https://www.terraform.io/docs/enterprise/saml/index.html)

* [Create a non-SSO admin account for recovery](https://www.terraform.io/docs/enterprise/saml/troubleshooting.html#create-a-non-sso-admin-account-for-recovery)
