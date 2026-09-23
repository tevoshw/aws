# AWS BOX

## 1. What is AWS BOX?

A mental model for everything you can do inside an AWS account. To access it, you need to log in using one of two methods:

- **Secret Key** — a fixed IAM user access key/secret key pair. Long-lived credentials, less recommended for daily use.
- **SSO (Single Sign-On / IAM Identity Center)** — generates temporary credentials via STS when you log in. Recommended approach, more secure (credentials expire automatically).

All access, regardless of the method, is governed by **IAM**: it defines *who* can do *what*, on *which* resource.

## 2. What's inside AWS BOX?

Everything falls into two big categories:

1. **API Services** — services you talk to directly through their API. No private network involved.
2. **VPC** — your private, isolated network, where network-bound resources live (subnets, EC2, RDS, etc.)

The key question to classify any service:

> "After calling the API, is there anything 'inside' I still need to access?"

- Only API → **global/managed service** (category 1)
- API + need to access an OS/network → lives **inside a VPC** (category 2)

---

## 3. API Services (Global)

These services are **not tied to a VPC**. You call the API and you already have full access — no private IP, no OS, no "inside" to enter.

### S3 (Simple Storage Service)
- Object storage — basically an "HD in the cloud."
- Stores files (objects) inside **buckets**.
- No real folder structure — keys simulate folders (`images/photo.png`), but it's flat underneath.
- Access only via API: `PutObject`, `GetObject`, `DeleteObject`, `ListObjects`.
- Common ML/data use: raw datasets, trained model checkpoints, data lake source for pipelines.

### DynamoDB
- Managed **NoSQL** database (key-value / document style).
- No JOINs, no traditional SQL — schema is flexible.
- Structure: **Table** → **Item** (a JSON-like row) → identified by **Partition Key** (+ optional **Sort Key**).
- Access via API: `PutItem`, `GetItem`, `Query`, `Scan`.
- Common ML/data use: low-latency feature store, pipeline metadata, real-time app state.

### IAM (Identity and Access Management)
- Global — not tied to any region.
- Controls **who** (users, roles) can do **what** (permissions), and **where** (which resource).
- Built from **Policies** (JSON documents) attached to **Users**, **Roles**, or **Groups**.
- The "gatekeeper" for every other AWS service — nothing happens without IAM approval first.

### Route 53
- AWS's **DNS** service.
- Translates domain names (`mysite.com`) into IP addresses.
- Can also register domains and route traffic to AWS resources (EC2, S3, Load Balancer, CloudFront).
- Key concepts: **Hosted Zone**, **Records** (`A`, `CNAME`, `Alias`), **Health Checks**, **Routing Policies**.

### CloudWatch
- **Monitoring and observability** service.
- Collects **Metrics** (CPU, latency, request counts), **Logs** (from Lambda, EC2, ECS), triggers **Alarms**, and builds **Dashboards**.
- Common ML/data use: monitor training instance CPU/GPU usage, view Lambda error logs, alarm on a growing SQS queue.

### Other common global services (quick reference)
- **CloudFront** — CDN
- **SNS / SQS** — messaging and queues
- **KMS** — encryption key management
- **ECR** — Docker image registry (the registry itself is global; what *runs* the image, like EC2/Fargate, can live in a VPC)

---

## 4. VPC (Virtual Private Cloud)

Your private, isolated network inside AWS — like having your own virtual datacenter, with full control over IPs, subnets, routing, and access rules.

**Rule of thumb:** if a resource has a private IP (an ENI attached to a subnet), it's "inside" the VPC.

### Core components

| Component | What it does |
|---|---|
| **CIDR block** | The VPC's overall IP range (e.g., `10.0.0.0/16`) |
| **Subnets** | Subdivisions of the VPC — **public** (route to internet) or **private** (no direct internet route) |
| **Route Tables** | Define where traffic from each subnet goes |
| **Internet Gateway (IGW)** | Entry/exit point to the public internet |
| **NAT Gateway** | Lets a private subnet reach the internet outbound, without being reachable from outside |
| **Security Groups** | Firewall at the resource/instance level |
| **NACLs** | Firewall at the subnet level |

### Does "inside the VPC" mean I need extra access to get "inside" the resource?

Not necessarily — these are two separate things:

1. **Being in the VPC** = has a private IP, is part of the network
2. **Having an accessible "inside" (OS)** = depends on the service type

| Service | In the VPC? | Needs something extra to access "inside" (OS)? |
|---|---|---|
| **EC2** | Yes | Yes — SSM Session Manager or SSH |
| **RDS** | Yes | No — connect directly via DB endpoint (port 5432/3306), OS is never exposed |
| **Fargate** | Yes | No — managed container, no exposed OS |
| **Lambda** (if configured with VPC access) | Yes, optionally | No — only executes code, no OS |
| **EKS/ECS nodes** | Yes | Yes (nodes run on EC2 underneath), but usually you work with the container, not the node |

**Practical rule:** only when a service runs on a **real EC2 instance underneath** can you actually get "inside" it (via SSM/SSH). Everything else — even inside the VPC — is accessed purely through its API/endpoint, the same way you'd talk to a global service like S3.

---

## 5. Summary Diagram (conceptual)

```
AWS BOX
├── Login: Secret Key or SSO (governed by IAM)
│
├── API Services (Global, no VPC)
│   ├── S3          → object storage, API-only
│   ├── DynamoDB     → NoSQL DB, API-only
│   ├── IAM          → access control
│   ├── Route 53     → DNS
│   └── CloudWatch   → monitoring/logs
│
└── VPC (Private Network)
    ├── Subnets (public / private)
    ├── Route Tables / IGW / NAT Gateway
    ├── Security Groups / NACLs
    └── Resources
        ├── EC2            → has accessible OS (SSM/SSH)
        ├── RDS            → API/endpoint only
        ├── Fargate        → API/endpoint only
        └── Lambda (VPC)   → API/endpoint only
```