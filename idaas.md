---

# Identity and Access Management (IAM) & IDaaS Notes

## What is IAM?

I define **IAM (Identity and Access Management)** as

> **Giving the right person access to the right resource at the right time for the right reason.**

Simple flow:

```text
Right User
   ↓
Right Resource
   ↓
Right Permission
```

Example:
- Devanshi can access S3
- Devanshi cannot delete EC2

That is IAM.

---

# What is IDaaS?

**IDaaS = Identity as a Service**

Meaning:
I outsource identity management to cloud providers.

Simple flow:

```text
User Login
   ↓
Cloud Identity Provider
   ↓
Authentication Success
```

Examples:
- Okta
- Auth0
- AWS IAM Identity Center

---

# 1. Form Authentication

This is the most basic login method.

Flow:

```text
User → Login Page → Username + Password → Database Validation → Access
```

Example:
- Instagram login
- College portal login

---

## Password Storage

Passwords should never be stored in plain text.

Instead:

```text
mypassword123 → hashed value
```

Example:
`mypassword123` → `kshd872js8d...`

This improves security.

---

## Disadvantages of Form Authentication

### 1. Too many accounts
I need separate accounts everywhere:
- Gmail
- Amazon
- College portal

This creates password fatigue.

---

### 2. Poor third-party integration
Hard to connect with other systems.

Not scalable.

---

# 2. Active Directory (AD)

I think of **Active Directory** as:

> Organization's central user database

It stores:
- usernames
- passwords
- roles
- devices
- departments

Example:

```text
Devanshi
 ├── password
 ├── role = student
 └── department = CSE
```

---

## Benefits of Active Directory

- centralized user management
- stronger security
- easier onboarding/offboarding

Example:
Add user once → gets access everywhere.

---

# 3. Single Sign-On (SSO)

Meaning:

> Login once, access many apps.

Example:

```text
Login to Google
   ↓
Gmail
Drive
YouTube
```

Only one login needed.

---

## Popular SSO Providers

- Okta
- Auth0
- Keycloak
- VMware Workspace One
- Google Identity

---

## Advantages of SSO

- fewer passwords
- less password fatigue
- faster login
- easier onboarding
- fewer helpdesk tickets

---

## Disadvantage of SSO

**Single point of failure**

If SSO fails:
all connected apps fail.

Risky if not secured.

---

# 4. LDAP

LDAP full form:

**Lightweight Directory Access Protocol**

Important:

> LDAP is not a database.  
> LDAP is a protocol.

It is used to access directory data.

Flow:

```text
Application
   ↓
LDAP Request
   ↓
Directory Server
   ↓
Response
```

Runs over:
- TCP/IP

---

## Example

Outlook searching employee directory:

Search:
`Find Devanshi`

Returns:
- email
- department
- phone

---

# LDAP vs Active Directory

| Active Directory | LDAP |
|------------------|------|
| database | protocol |
| stores users | accesses users |
| Microsoft product | industry standard |

Easy memory trick:

**AD stores. LDAP talks.**

---

# Directory Structure

Directories are tree-like.

Example:

```text
company.com
 ├── HR
 ├── Finance
 └── Engineering
      └── Devanshi
```

Easy to organize users.

---

# Advantages of Cloud IAM

## 1. Single Access Control Interface
One dashboard controls all users.

---

## 2. Enhanced Security
Supports:
- MFA
- policies
- role-based access

---

## 3. Resource-Level Access Control
Fine-grained permissions.

Example:
- can read file
- cannot delete file

---

# Final Understanding

I use:
- **Form Authentication** for simple login
- **Active Directory** to store users
- **LDAP** to access directory data
- **SSO** for one-login-many-apps
- **IAM/IDaaS** to secure everything in the cloud

**Identity is the security backbone of cloud computing.**
