# Web Infrastructure Design

This project is part of a hands on, ALX software engineering curriculum where we **design, scale, and secure web infrastructure** using real-world principles. Through a progressive series of tasks, we simulate what it’s like to architect production grade systems from scratch just like a **DevOps** or **SRE** engineer would in industry.

##  Task 0: Simple Web Stack

### Objective
Design a basic single-server infrastructure that hosts `www.foobar.com` using a LAMP-style setup with modern components.

### Components
- 1 Physical/Virtual Server
- Nginx (Web Server)
- Application Server (e.g., PHP-FPM or Gunicorn)
- MySQL Database
- Application Files (codebase)
- DNS configuration: A record for `www.foobar.com → 8.8.8.8`

### Key Concepts
- Role of DNS and A records
- Flow of HTTP requests through Nginx to the app server
- MySQL integration for persistent storage

### Limitations
- Single Point of Failure
- Downtime during maintenance or deployment
- No horizontal scalability

📸 [Whiteboard Screenshot ](https://ibb.co/gLYwr62M)


##  Task 1: Distributed Web Infrastructure

### Objective
Extend the setup to a three-server infrastructure for load balancing and better fault tolerance.

### Components
- Load Balancer (HAProxy)
- Web Server (Nginx)
- Application Server (with app code)
- MySQL Database
- Domain: `www.foobar.com`

### Load Balancing
- **Algorithm**: Round Robin
- **Mode**: Active-Active (distributes live traffic across nodes)

### Concepts
- Improved fault tolerance and performance
- Basics of scaling web apps horizontally
- Database cluster architecture: Primary-Replica explained (even if only Primary is implemented here)

### Infrastructure Issues
- Load balancer is still a SPOF without failover
- No monitoring or firewall
- No HTTPS encryption

📸 [Whiteboard Screenshot](https://ibb.co/LzYbzLg4K)


##  Task 2: Secured and Monitored Infrastructure

### Objective
Secure the architecture with firewalls and HTTPS; add monitoring clients.

### Components Added
- 3 Firewalls (protecting LB, Web, and App servers)
- SSL Certificate (HTTPS on Nginx)
- 3 Monitoring Clients (e.g., Sumologic agents on each server)

### Key Concepts
- TLS/SSL and HTTPS benefits
- Infrastructure-level monitoring for logs, health, and usage
- Role of firewalls in server-level security

📸 [Whiteboard Screenshot](https://ibb.co/wNdJGG49  )



##  Task 3: Scale Up

### Objective
Fully decouple services and configure a failover-ready, clustered setup.

### Components
- Load Balancer Cluster (2 HAProxy servers in Active-Passive mode)
- Separate Web Server
- Separate Application Server
- Separate MySQL Database Server
- 4 total servers (1 per role)

### Benefits
- Clear separation of concerns
- Horizontal scaling opportunities
- High availability with LB clustering

### Concepts
- Active vs Passive load balancing
- Why modular infrastructure increases maintainability
- Comparing Web Server vs Application Server roles

📸 [Whiteboard Screenshot](https://ibb.co/bMXThPwS)


##  Definitions

| Term | Description |
|------|-------------|
| Web Server | Handles HTTP requests, static files, and SSL termination (e.g., Nginx) |
| Application Server | Runs backend business logic using your codebase |
| Load Balancer | Routes traffic to servers using algorithms like Round Robin |
| DNS A Record | Maps domain to server IP |
| Primary DB | Handles writes |
| Replica DB | Handles reads, replicates from Primary |

---

## ✅ Notes
- All diagrams were created based on whiteboarding sessions.
- Monitoring agents should be configured to collect system logs, HTTP metrics, and error traces.
- SSL certificates can be generated via Let's Encrypt for HTTPS setup.

