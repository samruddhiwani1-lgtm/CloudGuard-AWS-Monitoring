# ☁️ CloudGuard – Intelligent Cloud Monitoring & Auto-Healing System

## 📌 Project Title

**CloudGuard – Intelligent Cloud Monitoring & Auto-Healing System**

---

## 📖 Abstract

CloudGuard is an AWS-based cloud monitoring and auto-healing system designed to monitor the performance of a cloud server and automate recovery actions when a high CPU utilization condition is detected.

The system uses an Amazon EC2 instance running Ubuntu Linux and Apache Web Server to host a web application. Amazon CloudWatch continuously monitors the CPU utilization of the EC2 instance.

When CPU utilization reaches or exceeds a predefined threshold, a CloudWatch Alarm is configured to detect the abnormal condition. Amazon EventBridge is used to handle the alarm state-change event and invoke an AWS Lambda function. The Lambda function uses Python and the AWS SDK (`boto3`) to reboot the EC2 instance.

The project demonstrates important cloud computing concepts including cloud infrastructure, monitoring, automation, serverless computing, IAM permissions, event-driven architecture, network security, and automated recovery.

---

# 🎯 Problem Statement

Cloud servers may experience high CPU utilization because of heavy workloads, unexpected traffic, resource-intensive applications, or system processes.

If high resource utilization is not detected and handled quickly, it can affect application performance and availability.

Traditional monitoring systems may require a system administrator to manually identify the problem and restart or recover the server.

CloudGuard addresses this problem by creating an automated monitoring and recovery workflow using AWS services.

---

# 💡 Proposed Solution

CloudGuard continuously monitors the CPU utilization of an EC2 instance using Amazon CloudWatch.

The system follows this process:

1. A web application is hosted on an EC2 instance.
2. CloudWatch monitors the EC2 CPU utilization.
3. A CloudWatch Alarm checks whether CPU utilization crosses the defined threshold.
4. When the alarm enters the required state, EventBridge receives the alarm event.
5. EventBridge invokes the Lambda function.
6. Lambda uses Python and `boto3` to reboot the EC2 instance.
7. The EC2 server becomes available again after the reboot.
8. The website can then be accessed again.

---

# 🎯 Objectives

The main objectives of CloudGuard are:

- To deploy a web server on AWS EC2.
- To host a website using Apache Web Server.
- To monitor EC2 CPU utilization using Amazon CloudWatch.
- To configure an automated CPU threshold alarm.
- To use Amazon EventBridge for event-driven automation.
- To use AWS Lambda for automatic recovery.
- To configure IAM permissions securely.
- To understand AWS Security Groups and network access.
- To demonstrate cloud auto-healing concepts.
- To gain practical experience with AWS cloud services.
- To maintain the project using Git and GitHub.

---

# 🏗️ System Architecture

The overall CloudGuard architecture is:

```text
                         USER
                           │
                           │ HTTP
                           ▼
                 ┌─────────────────────┐
                 │    EC2 INSTANCE     │
                 │      Ubuntu         │
                 │                     │
                 │  Apache Web Server  │
                 │         │           │
                 │         ▼           │
                 │  CloudGuard Website │
                 └──────────┬──────────┘
                            │
                            │ CPU Metrics
                            ▼
                  ┌─────────────────────┐
                  │     CloudWatch      │
                  │  CPU Monitoring     │
                  └──────────┬──────────┘
                             │
                             │ CPU ≥ 70%
                             ▼
                  ┌─────────────────────┐
                  │  CloudWatch Alarm   │
                  │ CloudGuard-High-CPU │
                  └──────────┬──────────┘
                             │
                             │ Alarm Event
                             ▼
                  ┌─────────────────────┐
                  │    EventBridge      │
                  │  Alarm Trigger Rule │
                  └──────────┬──────────┘
                             │
                             │ Invoke
                             ▼
                  ┌─────────────────────┐
                  │    AWS Lambda       │
                  │ CloudGuard-         │
                  │ AutoHealing         │
                  └──────────┬──────────┘
                             │
                             │ Reboot
                             ▼
                  ┌─────────────────────┐
                  │    EC2 Recovery     │
                  │   Server Restored   │
                  └─────────────────────┘

