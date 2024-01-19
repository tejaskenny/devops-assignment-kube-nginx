
# Devops Assignment (EKS Kubernetes Deployment with Nginx Ingress)

This project automates the deployment of an Nginx Ingress Controller and a "Hello World" application on Amazon EKS using Ansible. The deployment includes setting up TLS termination with a self-signed certificate for secure communication.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Clone the Repository](#clone-the-repository)
  - [Run the Ansible Playbook](#run-the-ansible-playbook)
  - [Access the Application](#access-the-application)
- [Troubleshooting](#troubleshooting)


## Overview

Automating the deployment of Kubernetes resources can be complex. This project streamlines the process of setting up a basic environment for deploying applications on Amazon EKS. It uses Ansible, a powerful automation tool, to provision the Nginx Ingress Controller, deploy a sample application, and configure TLS termination.

## Prerequisites

List any prerequisites or dependencies that users need to have installed before running the Ansible playbook.

- [Ansible](https://www.ansible.com/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [AWS CLI](https://aws.amazon.com/cli/)
- [eksctl](https://eksctl.io/)
- [Helm](https://helm.sh/)



Additionally, install the following Ansible Galaxy collections:

```bash
ansible-galaxy collection install community.general
ansible-galaxy collection install community.kubernetes


## Getting Started

### Clone the Repository

```bash
git clone https://github.com/your-username/your-repository.git
cd your-repository
```
### Run the Ansible Playbook
```bash
ansible-playbook ansible-deploy.yaml
```

### Access the Application
```bash
kubectl get services -o wide -w -n ingress-nginx
https://<external-ip>
```

## Troubleshooting

Ansible Playbook Execution:

Issue: The Ansible playbook fails during execution.
Troubleshooting Steps:
Check if Ansible is correctly installed on your machine.
Ensure that your AWS CLI configuration is set up correctly.
Verify the connectivity to your EKS cluster.
Examine the Ansible playbook logs for error messages and investigate accordingly.
Nginx Ingress Controller Deployment:

Issue: Nginx Ingress Controller deployment is not successful.
Troubleshooting Steps:
Check Helm installation and repository access.
Review Helm chart values to ensure they match your requirements.
Inspect Nginx Ingress Controller pods for any issues using kubectl get pods -n ingress-nginx.
Application Deployment:

Issue: "Hello World" application deployment fails.
Troubleshooting Steps:
Confirm that the Kubernetes YAML files for the application are correct.
Check if the required container image is accessible and correctly specified.
Examine the application deployment logs for any issues using kubectl logs <pod-name>.
TLS Termination:

Issue: TLS termination is not working, or the application is not accessible over HTTPS.
Troubleshooting Steps:
Verify that the TLS Secret is created in the correct namespace.
Check if the certificate files (tls.crt and tls.key) are correctly base64-encoded in the Secret.
Ensure that the Ingress resource is configured to use the TLS Secret.
Networking:

Issue: Unable to access the application externally.
Troubleshooting Steps:
Confirm that the Nginx Ingress Controller service has an external IP.
Check if there are any network policies blocking access to the Ingress or application services.
Certificate Issues:

Issue: SSL/TLS certificate errors in the browser.
Troubleshooting Steps:
Confirm that the certificate common name matches the domain you are using.
Ensure that the self-signed certificate is correctly generated and applied to the Ingress.
AWS EKS Cluster:

Issue: Issues related to the EKS cluster itself.
Troubleshooting Steps:
Check the EKS cluster status using eksctl.
Review AWS CloudWatch logs for any relevant error messages.
