# AWS Load Balancers Study Guide

## Table of Contents
1. [Introduction to AWS Load Balancers](#introduction-to-aws-load-balancers)
2. [Application Load Balancer (ALB)](#application-load-balancer-alb)
3. [Network Load Balancer (NLB)](#network-load-balancer-nlb)
4. [Classic Load Balancer (CLB)](#classic-load-balancer-clb)
5. [Comparison Table](#comparison-table)
6. [Essential Exam Concepts](#essential-exam-concepts)

---

## Introduction to AWS Load Balancers

### What are Load Balancers?

AWS Elastic Load Balancing (ELB) automatically distributes incoming application traffic across multiple targets, such as EC2 instances, containers, and IP addresses, in one or more Availability Zones. This increases the availability and fault tolerance of your applications.

### Core Concepts

- **Load Balancer**: Single point of contact for clients
- **Listeners**: Check for connection requests using specific protocol and port
- **Target Groups**: Route requests to registered targets (EC2 instances, containers, IP addresses, Lambda functions)
- **Health Checks**: Monitor target health and route traffic only to healthy targets
- **Availability Zones**: Distribute traffic across multiple AZs for high availability

### When to Use Load Balancers

- **High Availability**: Distribute traffic across multiple targets
- **Fault Tolerance**: Automatically route around unhealthy targets
- **Scalability**: Handle varying traffic loads
- **SSL/TLS Termination**: Offload encryption/decryption from application servers
- **Content-based Routing**: Route requests based on URL path, host header, or other criteria

---

## Application Load Balancer (ALB)

### Overview
Application Load Balancer operates at **Layer 7** (HTTP/HTTPS) of the OSI model and provides advanced request routing capabilities.

### Key Features

#### Layer 7 Load Balancing
- **Protocols**: HTTP, HTTPS
- **Ports**: 1-65535
- **Advanced Routing**: Path-based, host-based, header-based, query string routing

#### Target Types
- EC2 instances
- IP addresses
- Lambda functions
- ECS tasks
- EKS pods

#### Advanced Routing Capabilities
- **Path-based routing**: Route based on URL path (`/api/*`, `/images/*`)
- **Host-based routing**: Route based on host header (`api.example.com`, `www.example.com`)
- **Header-based routing**: Route based on HTTP headers
- **Query string routing**: Route based on query parameters
- **HTTP method routing**: Route based on GET, POST, etc.

#### Key Features for Exam
- **Content-based routing**: Most advanced routing capabilities
- **WebSocket support**: Full WebSocket support
- **HTTP/2 support**: Native HTTP/2 support
- **Sticky sessions**: Session affinity using cookies
- **Cross-Zone Load Balancing**: Enabled by default (no additional cost)

### Best Use Cases
- Web applications requiring advanced routing
- Microservices architectures
- Container-based applications
- Applications needing content-based routing
- WebSocket applications

### Important Limitations
- **Layer 7 only**: Cannot handle TCP/UDP traffic
- **No static IP**: IP address can change
- **No source IP preservation**: Client IP is not preserved
- **WebSocket health checks**: Not supported

### Pricing
- **LCU (Load Balancer Capacity Units)**: Based on new connections, active connections, and processed bytes
- **Cross-Zone Load Balancing**: No additional cost
- **Data processing**: Charged per GB processed

---

## Network Load Balancer (NLB)

### Overview
Network Load Balancer operates at **Layer 4** (TCP/UDP/TLS) of the OSI model and provides ultra-low latency and high throughput.

### Key Features

#### Layer 4 Load Balancing
- **Protocols**: TCP, UDP, TCP_UDP, TLS
- **Ports**: 1-65535
- **Ultra-low latency**: Sub-millisecond latency
- **High throughput**: Millions of requests per second

#### Target Types
- EC2 instances
- IP addresses
- Application Load Balancers (for hybrid architectures)

#### Key Features for Exam
- **Static IP support**: Assign Elastic IP addresses
- **Source IP preservation**: Client IP is preserved
- **Extreme performance**: Handle millions of requests per second
- **Cross-Zone Load Balancing**: Disabled by default (additional cost)
- **Zonal isolation**: Can operate in single AZ if needed

### Best Use Cases
- High-performance applications
- Gaming applications
- IoT applications
- Real-time applications
- Applications requiring static IP
- TCP/UDP-based applications

### Important Limitations
- **No content-based routing**: Cannot route based on URL path or headers
- **No SSL/TLS termination**: Must handle at application level
- **Cross-Zone Load Balancing**: Additional cost when enabled
- **No sticky sessions**: Cannot maintain session affinity

### Pricing
- **NLCU (Network Load Balancer Capacity Units)**: Based on new connections, active connections, and processed bytes
- **Cross-Zone Load Balancing**: Additional cost when enabled
- **Static IP**: No additional cost for Elastic IP assignment

---

## Classic Load Balancer (CLB)

### Overview
Classic Load Balancer is the **legacy load balancer** that operates at both Layer 4 and basic Layer 7. AWS recommends migrating to ALB or NLB.

### Key Features

#### Dual Layer Support
- **Layer 4**: TCP load balancing
- **Layer 7**: Basic HTTP/HTTPS load balancing

#### Target Types
- EC2 instances only
- No support for IP addresses, Lambda, or containers

#### Key Features for Exam
- **Legacy status**: Being phased out
- **Basic routing**: Limited routing capabilities compared to ALB
- **Sticky sessions**: Session affinity support
- **Cross-Zone Load Balancing**: Available but not enabled by default

### Why AWS Recommends Migration
- **Limited features**: Basic functionality compared to modern load balancers
- **No advanced routing**: Cannot do path-based or host-based routing
- **Limited target types**: Only EC2 instances
- **No modern protocols**: No HTTP/2 or WebSocket support
- **Higher costs**: More expensive than ALB/NLB for equivalent functionality

### When It Might Appear on Exam
- **Legacy scenarios**: Questions about existing infrastructure
- **Migration questions**: When to migrate from CLB to ALB/NLB
- **Cost optimization**: Understanding when to upgrade

### Pricing
- **Hourly charges**: Based on hours the load balancer is running
- **Data processing**: Charged per GB processed
- **Cross-Zone Load Balancing**: Additional cost when enabled

---

## Comparison Table

| Feature | ALB | NLB | CLB |
|---------|-----|-----|-----|
| **OSI Layer** | Layer 7 (HTTP/HTTPS) | Layer 4 (TCP/UDP/TLS) | Layer 4 & 7 |
| **Protocols** | HTTP, HTTPS | TCP, UDP, TCP_UDP, TLS | HTTP, HTTPS, TCP, SSL |
| **Target Types** | EC2, IP, Lambda, ECS, EKS | EC2, IP, ALB | EC2 only |
| **Routing** | Advanced (path, host, header) | Basic (round-robin) | Basic (round-robin) |
| **Static IP** | No | Yes (Elastic IP) | No |
| **Source IP Preservation** | No | Yes | No |
| **WebSocket Support** | Yes | Yes | No |
| **HTTP/2 Support** | Yes | No | No |
| **Sticky Sessions** | Yes | No | Yes |
| **Cross-Zone LB** | Enabled by default (free) | Disabled by default (cost) | Available (cost) |
| **Health Checks** | HTTP/HTTPS | TCP/HTTP/HTTPS | HTTP/HTTPS/TCP |
| **SSL Termination** | Yes | No | Yes |
| **Performance** | High | Ultra-high | Medium |
| **Cost Model** | LCU | NLCU | Hourly + data |

### Decision Framework

**Choose ALB when:**
- Need advanced routing (path-based, host-based)
- Using microservices architecture
- Need WebSocket support
- Want HTTP/2 support
- Using containers or Lambda functions

**Choose NLB when:**
- Need ultra-high performance
- Require static IP address
- Need source IP preservation
- Using TCP/UDP protocols
- Building gaming or IoT applications

**Choose CLB when:**
- Migrating from existing CLB (temporary)
- Need basic Layer 4 and 7 functionality
- Legacy application requirements

---

## Essential Exam Concepts

### Cross-Zone Load Balancing

**ALB**: 
- **Enabled by default** at no additional cost
- Distributes traffic evenly across all AZs
- Automatically handles AZ failures

**NLB**: 
- **Disabled by default** to reduce costs
- When enabled, incurs additional charges
- Distributes traffic across all AZs when enabled

**CLB**: 
- **Available but not enabled by default**
- Additional cost when enabled
- Can be enabled per AZ

### Connection Draining / Deregistration Delay

**Purpose**: Gracefully remove targets from service without dropping active connections

**ALB**: 
- **Deregistration Delay**: 0-3600 seconds (default: 300)
- Allows existing connections to complete
- New connections are not sent to draining targets

**NLB**: 
- **Connection Draining**: 0-3600 seconds (default: 300)
- Similar to ALB but for Layer 4 connections

**CLB**: 
- **Connection Draining**: 0-3600 seconds (default: 300)
- Legacy implementation

### Sticky Sessions (Session Affinity)

**ALB**: 
- **Application-based cookies**: AWSALB, AWSALBCORS
- **Duration-based cookies**: AWSALBAPP
- **Custom cookies**: Can specify custom cookie name

**NLB**: 
- **Not supported**: No session affinity
- Each request can go to any healthy target

**CLB**: 
- **Duration-based cookies**: AWSELB
- **Application-based cookies**: Custom application cookies

### SSL/TLS Termination

**ALB**: 
- **Full SSL/TLS termination**: Handles encryption/decryption
- **SNI support**: Multiple certificates per listener
- **Security policies**: Configurable cipher suites
- **Mutual TLS**: Client certificate authentication

**NLB**: 
- **TLS passthrough**: Forwards encrypted traffic to targets
- **No SSL termination**: Targets must handle SSL/TLS
- **TLS listeners**: Can terminate TLS but limited features

**CLB**: 
- **SSL termination**: Basic SSL/TLS termination
- **Limited certificate management**: One certificate per listener
- **No SNI support**: Cannot use multiple certificates

### Health Checks

**ALB**: 
- **HTTP/HTTPS health checks**: Most common
- **Health check path**: Configurable endpoint
- **Response codes**: 200-399 considered healthy
- **Timeout**: 2-120 seconds (default: 5)
- **Interval**: 5-300 seconds (default: 30)

**NLB**: 
- **TCP health checks**: Basic connectivity
- **HTTP/HTTPS health checks**: Application-level checks
- **Health check port**: Can differ from traffic port
- **Timeout**: 2-120 seconds (default: 10)

**CLB**: 
- **HTTP/HTTPS health checks**: Application-level checks
- **TCP health checks**: Basic connectivity
- **Health check path**: Configurable endpoint
- **Response codes**: 200-399 considered healthy

### Security Groups

**ALB**: 
- **Security groups required**: Must configure for HTTP/HTTPS traffic
- **Target security groups**: Separate from load balancer
- **Port configuration**: 80, 443, and health check ports

**NLB**: 
- **No security groups**: Cannot use security groups
- **Target security groups**: Must configure on targets
- **Network ACLs**: Use for network-level security

**CLB**: 
- **Security groups supported**: Can use security groups
- **Target security groups**: Separate from load balancer
- **Port configuration**: Traffic and health check ports

### Access Logs

**ALB**: 
- **S3 logging**: Store logs in S3 bucket
- **Log format**: Detailed request information
- **Log fields**: Timestamp, client IP, target IP, request processing time
- **Cost**: Additional charges for log storage

**NLB**: 
- **CloudWatch Logs**: Store logs in CloudWatch
- **Log format**: Connection-level information
- **Log fields**: Timestamp, client IP, target IP, connection duration
- **Cost**: CloudWatch Logs charges

**CLB**: 
- **S3 logging**: Store logs in S3 bucket
- **Log format**: Basic request information
- **Log fields**: Timestamp, client IP, target IP, response time
- **Cost**: Additional charges for log storage

---

## Exam Tips

### Common Scenario Questions

1. **Microservices Architecture**: Choose ALB for path-based routing
2. **High Performance Gaming**: Choose NLB for ultra-low latency
3. **Static IP Requirement**: Choose NLB with Elastic IP
4. **WebSocket Support**: Choose ALB or NLB (not CLB)
5. **Legacy Migration**: Understand when to migrate from CLB
6. **Cost Optimization**: Consider ALB vs NLB pricing models
7. **Health Check Configuration**: Know default values and customization options
8. **Cross-Zone Load Balancing**: Understand when it's enabled by default and costs

### Key Differences to Remember

- **ALB**: Layer 7, advanced routing, WebSocket, HTTP/2, cross-zone enabled by default
- **NLB**: Layer 4, ultra-high performance, static IP, source IP preservation, cross-zone disabled by default
- **CLB**: Legacy, basic features, being phased out, limited target types

### Pricing Considerations

- **ALB**: LCU-based pricing, cross-zone included
- **NLB**: NLCU-based pricing, cross-zone additional cost
- **CLB**: Hourly + data processing, cross-zone additional cost

---

*This study guide covers the essential concepts for AWS Solutions Architect Associate (SAA-C03) certification regarding Load Balancers. Focus on understanding the differences between ALB, NLB, and CLB, and when to use each type based on specific requirements.*
