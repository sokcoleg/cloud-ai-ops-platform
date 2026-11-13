# Cloud AI Ops Platform

Production-like AWS CloudOps platform for deploying, observing, troubleshooting, and automating cloud workloads with AI-assisted incident analysis.

## Project Goal

The goal of this project is to demonstrate practical Cloud / Infrastructure Engineering skills rather than build a standalone demo application.

The platform will evolve from a manually configured AWS environment into an automated, observable, secure, and reproducible cloud platform.

## Current Stage — v0.1

The first stage focuses on Linux, EC2, networking, and service troubleshooting.

Completed so far:

- Amazon EC2 running Amazon Linux 2023
- Nginx installation and service management
- HTTP access over port 80
- Security Group configuration
- Public and private IP basics
- Subnet and route table verification
- Internet Gateway verification
- Network ACL verification
- Service management with systemd
- Port inspection with `ss`
- Local service testing with `curl`
- Nginx configuration validation with `nginx -t`
- Service log inspection with `journalctl`
- Recovery from a broken Nginx configuration

## Planned Architecture

```text
User / Load Generator
        |
        v
Route 53 / ALB
        |
        v
Containerized API
        |
        v
       SQS
        |
        v
      Worker
        |
        +----> DynamoDB / S3

CloudWatch + EventBridge
        |
        v
Incident / Operations Layer
        |
        v
Amazon Bedrock
```

The workload exists to generate real operational signals and failure scenarios.

The core of the project is the cloud platform around it:

- Networking
- IAM and security
- Linux operations
- Monitoring and observability
- Infrastructure as Code
- CI/CD
- Incident troubleshooting
- Automation
- Cost optimization
- AI-assisted operations

## Roadmap

1. Linux administration and troubleshooting
2. AWS networking
3. IAM and security
4. AWS CLI
5. Cloud Operations lab
6. Python and boto3
7. API + asynchronous worker workload
8. Docker
9. Terraform
10. GitHub Actions + AWS OIDC
11. CloudWatch and EventBridge
12. Incident workflows
13. Amazon Bedrock integration
14. Security hardening and cost optimization

## Engineering Principles

- Least privilege IAM
- No long-lived AWS credentials in source control
- Infrastructure as Code
- Observable services
- Reproducible deployments
- Documented incidents and root-cause analysis
- Cost-aware architecture
- Clear incremental Git history

## Portfolio Focus

**Build → Deploy → Observe → Break → Diagnose → Recover → Automate**

## Status

Work in progress.

This repository intentionally documents the platform from its first manual EC2/Linux stage through automation, containerization, Infrastructure as Code, CI/CD, observability, and AI infrastructure.
