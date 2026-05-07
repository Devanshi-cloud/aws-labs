## 🔐 IAM User & Access Related

```bash
aws iam create-user --user-name Ram
```

Attach ReadOnly policy:

```bash
aws iam attach-user-policy \
--user-name Ram \
--policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess
```

List user policies:

```bash
aws iam list-attached-user-policies --user-name Ram
```

Detach policy:

```bash
aws iam detach-user-policy \
--user-name Ram \
--policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess
```

---

## 🧾 Credential Report

Generate report:

```bash
aws iam generate-credential-report
```

Download report:

```bash
aws iam get-credential-report
```

---

## 🔑 MFA (mostly console-based, but CLI concept)

List MFA devices:

```bash
aws iam list-mfa-devices --user-name Ram
```

---

## 👥 Roles & Trust Policy

Create role:

```bash
aws iam create-role \
--role-name customiamrole \
--assume-role-policy-document file://trust-policy.json
```

Attach policy to role:

```bash
aws iam attach-role-policy \
--role-name customiamrole \
--policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess
```

Update trust relationship:

```bash
aws iam update-assume-role-policy \
--role-name customiamrole \
--policy-document file://trust-policy.json
```

---

## 🔄 Assume Role (Cross-account)

```bash
aws sts assume-role \
--role-arn arn:aws:iam::<ACCOUNT_ID>:role/customiamrole \
--role-session-name crossAccountSession
```

---

## 🔍 IAM Access Analyzer

Enable analyzer:

```bash
aws accessanalyzer create-analyzer \
--analyzer-name MyAnalyzer \
--type ACCOUNT
```

List findings:

```bash
aws accessanalyzer list-findings --analyzer-name MyAnalyzer
```

---

## 🖥️ EC2 Commands

List instances:

```bash
aws ec2 describe-instances
```

Stop instance:

```bash
aws ec2 stop-instances --instance-ids i-xxxxxxxxxxxx
```

---

## 🪣 S3 Commands

Create bucket:

```bash
aws s3 mb s3://iam-test-user-name
```

List buckets:

```bash
aws s3 ls
```

Upload file:

```bash
aws s3 cp file.txt s3://iam-test-user-name/
```

List objects:

```bash
aws s3 ls s3://iam-test-user-name
```

Delete object:

```bash
aws s3 rm s3://iam-test-user-name/file.txt
```

Empty bucket:

```bash
aws s3 rm s3://iam-test-user-name --recursive
```

Delete bucket:

```bash
aws s3 rb s3://iam-test-user-name
```

---

## 🔐 Profile / Login (if used)

```bash
aws configure
```

---

If you want, I can next convert this into:

* **viva answers (very important for exams)**
* or **short “I did this lab” explanation in 5–6 lines**
* or **proper lab file format (ready to submit PDF style)**
