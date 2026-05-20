# ⚡ Amazon Compute Services — My Understanding

> I use **Amazon Compute Services** when I want AWS to run my applications, websites, containers, or code — without worrying about physical servers.

**Think:**
```
"I need compute power" → AWS gives me multiple ways → Choose based on use case.
```

---

## 📌 Table of Contents

- [AWS Lambda — Serverless Compute](#1-aws-lambda--easiest-serverless-compute)
- [Amazon Lightsail — Easy VPS](#2-amazon-lightsail--easiest-vps)
  - [Lightsail vs EC2](#lightsail-vs-ec2)
- [Amazon EC2 — Full Control Server](#3-amazon-ec2--full-control-server)
- [Final Memory Trick](#-final-memory-trick)

---

## 1. AWS Lambda — Easiest Serverless Compute

> I use **AWS Lambda** when I want to run code **without managing servers**.

```
Just upload code → Define trigger → AWS runs it automatically
```

### How it works

| Step | Action |
|---|---|
| 1 | Write your function (Python, Node.js, Java, etc.) |
| 2 | Upload to Lambda |
| 3 | Define a trigger |
| 4 | AWS runs it automatically when triggered |

### Trigger Examples

```
File uploaded to S3       →  Lambda runs
API request comes in      →  Lambda runs
Scheduled task (cron)     →  Lambda runs
```

### Why I use Lambda

| Benefit | Details |
|---|---|
| ✅ No server management | Zero infra to set up or maintain |
| ✅ Auto scaling | Handles 1 request or 1 million — automatically |
| ✅ Pay only when code runs | No idle cost |
| ✅ Great for microservices | Small, independent, event-driven functions |
| ✅ Great for automation | Triggered by S3, API Gateway, EventBridge, etc. |

> 💡 **Simple line:** _"Write function → deploy → AWS handles infrastructure."_

---

## 2. Amazon Lightsail — Easiest VPS

> I use **Amazon Lightsail** when I need a simple virtual server (VPS).

**Think:**
```
Like renting a ready-made house instead of building one from scratch.
```

### Good for

- 🌐 Websites & blogs
- 📰 WordPress
- 🧪 Student projects
- 🚀 Startup MVPs
- 📦 Small apps

### Why I use Lightsail

| Benefit | Details |
|---|---|
| ✅ Fast setup | Server ready in ~2 minutes |
| ✅ Easy UI | No complex AWS console navigation |
| ✅ Predictable pricing | Fixed monthly cost — no surprise bills |
| ✅ Free trial available | Great for learning and prototyping |
| ✅ Preconfigured templates | WordPress, LAMP, Node.js, etc. |

### Services Inside Lightsail

| Service | Purpose |
|---|---|
| **Compute Instances** | Launch virtual machines |
| **Containers** | Run containerized apps |
| **Load Balancer** | Distribute incoming traffic |
| **Managed Databases** | MySQL / PostgreSQL |
| **Storage** | File and image backups |
| **CDN** | Faster global content delivery |
| **VPC Peering** | Connect with other AWS services |

> 💡 **Simple line:** _"Need a server in 2 minutes? Use Lightsail."_

---

### Lightsail vs EC2

| Feature | Amazon Lightsail | Amazon EC2 |
|---|---|---|
| **Ease of use** | Very easy | Advanced |
| **Pricing** | Fixed monthly | Pay-as-you-go |
| **Customization** | Limited | Full control |
| **Scaling** | Basic | Powerful |
| **Best for** | Beginners / Startups | Enterprises |

**My rule:**

```
Beginner or simple app  →  Lightsail
Advanced infrastructure →  EC2
```

---

## 3. Amazon EC2 — Full Control Server

> I use **Amazon EC2** when I need custom servers with full control.

**Think:**
```
Like building your own house exactly how you want it.
```

### When I choose EC2

- 🖥️ Custom server configuration
- 🐧 OS of my choice (Linux, Windows)
- 🔗 Full networking control
- 🏗️ Large-scale, enterprise systems

> _EC2 = maximum flexibility, maximum responsibility._

---

## 🧠 Final Memory Trick

```
Lambda     =  run code, no server
Lightsail  =  easy VPS
EC2        =  powerful custom server
```

### My Decision Formula

```
Small app / quick start      →  Lightsail
Event-driven / automated code →  Lambda
Enterprise infrastructure    →  EC2
```

> That's exactly how I choose compute on AWS. ✅

---

## Quick Reference — All Three

| Service | Best For | Server Management | Pricing Model |
|---|---|---|---|
| **AWS Lambda** | Event-driven code, automation | None (serverless) | Pay per execution |
| **Amazon Lightsail** | Simple websites, MVPs | Minimal | Fixed monthly |
| **Amazon EC2** | Custom, large-scale systems | Full | Pay-as-you-go |
