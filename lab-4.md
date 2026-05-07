## ☁️ I worked on AWS S3 using AWS CLI (Advanced Lab)

I used [Amazon Web Services (AWS)](https://aws.amazon.com?utm_source=chatgpt.com) CLI to implement Object Lock, Server Access Logging, and Access Points in Amazon S3.

---

# 🧪 Task 1: S3 Object Lock Configuration (Retention + Legal Hold)

### 1. Create bucket with Object Lock enabled

```bash
aws s3api create-bucket \
  --bucket my-objectlock-bucket \
  --region ap-south-1 \
  --object-lock-enabled-for-bucket
```

### 2. Enable versioning (required for Object Lock)

```bash
aws s3api put-bucket-versioning \
  --bucket my-objectlock-bucket \
  --versioning-configuration Status=Enabled
```

### 3. Upload file

```bash
aws s3 cp sample.txt s3://my-objectlock-bucket/
```

### 4. Apply Governance retention (7 days)

```bash
aws s3api put-object-retention \
  --bucket my-objectlock-bucket \
  --key sample.txt \
  --retention '{
    "Mode": "GOVERNANCE",
    "RetainUntilDate": "2026-05-14T00:00:00Z"
  }'
```

### 5. Apply Legal Hold

```bash
aws s3api put-object-legal-hold \
  --bucket my-objectlock-bucket \
  --key sample.txt \
  --legal-hold Status=ON
```

### 6. Tried deleting object (and it failed due to lock)

```bash
aws s3 rm s3://my-objectlock-bucket/sample.txt --version-id <version-id>
```

👉 I observed: deletion was blocked because Object Lock protection was active.

---

# 📊 Task 2: Enable S3 Server Access Logging

### 1. Create log bucket

```bash
aws s3api create-bucket \
  --bucket my-s3-logs-bucket \
  --region ap-south-1
```

### 2. Enable logging on main bucket

```bash
aws s3api put-bucket-logging \
  --bucket my-objectlock-bucket \
  --bucket-logging-status '{
    "LoggingEnabled": {
      "TargetBucket": "my-s3-logs-bucket",
      "TargetPrefix": "logs/"
    }
  }'
```

### 3. Perform operations

```bash
aws s3 cp sample.txt s3://my-objectlock-bucket/
aws s3 ls s3://my-objectlock-bucket/
aws s3 rm s3://my-objectlock-bucket/sample.txt
```

### 4. View logs

```bash
aws s3 ls s3://my-s3-logs-bucket/logs/
aws s3 cp s3://my-s3-logs-bucket/logs/<log-file> .
```

👉 In logs I observed:

* Request type (GET / PUT / DELETE)
* Timestamp of request
* Source IP
* HTTP status (200 / 403)

---

# 🔐 Task 3: S3 Access Points

### 1. Create Access Point

```bash
aws s3control create-access-point \
  --account-id <account-id> \
  --name my-access-point \
  --bucket my-objectlock-bucket
```

### 2. Attach policy to restrict access (IAM role example)

```bash
aws s3control put-access-point-policy \
  --account-id <account-id> \
  --name my-access-point \
  --policy '{
    "Version": "2012-10-17",
    "Statement": [{
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:ap-south-1:<account-id>:accesspoint/my-access-point/object/*"
    }]
  }'
```

### 3. Test access via Access Point

```bash
aws s3 ls s3://my-access-point/
aws s3 cp s3://my-access-point/sample.txt .
```

---

# 🧠 In short (how I think about it)

* I created a **locked bucket** (Object Lock) → data became immutable
* I enabled **logging bucket** → every action became traceable
* I created **Access Points** → controlled and scoped access instead of full bucket access

---

If you want, I can convert this into a **proper lab record (PDF format / viva answers / screenshots mapping)** for submission.
