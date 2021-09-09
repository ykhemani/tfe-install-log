# Configure SAML Single Sign On (SSO) with Azure Active Directory (AAD) - Part 2

## Configure Azure Active Directory (AAD) as the Identity Provider (IdP) for Terraform Enterprise (TFE)

---

### Create a New AAD *Non-Gallery* Application

#### In the Azure Portal, select Azure Active Directory

![](screenshots/26.png?raw=true)

#### In Azure Active Directory, select Enterprise applications

![](screenshots/27.png?raw=true)

#### Create a new application

![](screenshots/28.png?raw=true)

#### Select Create your own application

![](screenshots/29.png?raw=true)

#### Name your application (e.g. Terraform Enterprise) and seelct Non-gallery

![](screenshots/30.png?raw=true)

Click **Create**

---

### Set up Single Sign On

![](screenshots/31.png?raw=true)

#### Select SAML

![](screenshots/32.png?raw=true)

#### Edit Basic SAML Configuration

![](screenshots/33.png?raw=true)

##### Set Basic SAML Configuration as follows

![](screenshots/34.png?raw=true)

###### Identifier (Entity ID):

```
https://<TFE HOSTNAME>/users/saml/metadata
```

Note: You can also get the **Metadata (Audience) URL** value from the Terraform Enterprise SAML settings.


###### Reply URL (Assertion Consumer Service URL):

```
https://<TFE HOSTNAME>/users/saml/auth
```

Note: You can also get the **ACS consumer (recipient) URL** value from the Terraform Enterprise SAML settings.

###### Sign on URL

```
https://<TFE HOSTNAME>/
```

![](screenshots/35.png?raw=true)

###### Click save

![](screenshots/36.png?raw=true)

---

#### Set User Attributes & Claims

![](screenshots/37.png?raw=true)

##### Edit the Unique User IdentifieD (Name ID) Claim

![](screenshots/38.png?raw=true)

##### Set Source attribute to `user.mail`

![](screenshots/39.png?raw=true)

##### Click Save


#### Add new claim

![](screenshots/40.png?raw=true)

##### Set Name to `MemberOf` and Source Attribute to `user.assignedroles`

![](screenshots/41.png?raw=true)

##### Click Save

---

#### Download SAML Signing Certificate in base64 format

![](screenshots/42.png?raw=true)

#### Save the **Login URL** and **Logout URL**:

![](screenshots/43.png?raw=true)

---

### Create Teams in Terraform Enterprise

Create Teams in Terraform Enterprise as outlined on [https://www.terraform.io/docs/enterprise/saml/team-membership.html](https://www.terraform.io/docs/enterprise/saml/team-membership.html)

![](screenshots/44.png?raw=true)

---

### Configure Custom Roles for Team Membership Mapping

#### In the Azure Portal, search for and then click on **App Registrations**

![](screenshots/46.png?raw=true)

#### Under App registrations, select **All applications**

![](screenshots/47.png?raw=true)

#### Search for and select the application we created earlier.

![](screenshots/48.png?raw=true)

#### In the App Registration, select **Manifest** in the left sidebar.

![](screenshots/49.png?raw=true)

#### Add teams in this section:

![](screenshots/50.png?raw=true)

##### Note: Generate a unique guid for each role.

```
uuidgen | awk '{print tolower($0)}'
```

For example:

```
{
  "allowedMemberTypes": [
    "User"
  ],
  "displayName": "developers",
  "id": "62d7f45c-b69c-4eb5-8622-c3d1862c9fd3",
  "isEnabled": true,
  "description": "Developers Team",
  "value": "developers"
}
```

![](screenshots/51.png?raw=true)

---

### In Azure AD, assign roles to users and groups.

If you aren't using existing users/groups, please see [02_aad_sso_3_users_and_groups.md](02_aad_sso_3_users_and_groups.md) to create a test AD user/group.

#### Select user and assign developer role.

##### In the Enterprise application, select Users and groups

![](screenshots/57.png?raw=true)

##### Add new user/group

![](screenshots/58.png?raw=true)

##### Select user / group and role

![](screenshots/59.png?raw=true)

Click **Assign**.

---

### Create workspace and grant access to developer group

---

### Login as developer user and verify that you have privileges for that workspace.

---

## Reference

[https://www.terraform.io/docs/enterprise/saml/identity-provider-configuration-aad.html](https://www.terraform.io/docs/enterprise/saml/identity-provider-configuration-aad.html)

