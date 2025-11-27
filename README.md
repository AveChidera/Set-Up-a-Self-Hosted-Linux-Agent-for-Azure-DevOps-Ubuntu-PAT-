# **Set Up a Self-Hosted Linux Agent for Azure DevOps (Ubuntu + PAT)**

## Objective

Set up a **self-hosted Azure DevOps build agent** on an Ubuntu virtual machine running in Azure.

---

## What You Will Build

* One Ubuntu 22.04 VM (in AWS or Azure)
* A self-hosted **agent pool** in Azure DevOps (e.g., `SelfHostedPool`)
* An agent registered using a **Personal Access Token (PAT)**
* A test pipeline that confirms successful agent registration

---

## Instructions

### Step 1 — Create a Personal Access Token (PAT)

Generate a new PAT in Azure DevOps with scopes for **Agent Pools (Read & Manage)** and **Build (Read & Execute)**.
Store it securely; it will be required during agent registration.

### Step 2 — Create an Agent Pool

In Azure DevOps → Organization Settings → Agent Pools, create a new pool (for example `SelfHostedPool`).
This pool will host the agent you are about to register.

### Step 3 — Provision the VM

Create an Ubuntu 22.04/latest VM using either AWS or Azure.
Ensure SSH access is configured and ports 22 and 443 are open.
Verify connectivity with an SSH login.

### Step 4 — Install and Configure the Agent

On the VM, install the required dependencies and download the latest Azure Pipelines agent package for Linux.
Configure the agent using your organization URL and the PAT created earlier.
Register it under the agent pool you created.
Install and start the agent as a system service.

### Step 5 — Verify the Setup

Confirm that the service is running on the VM and that the agent appears **Online** in the Azure DevOps Agent Pool.

### Step 6 — Run a Test Pipeline

Create a simple Azure Pipeline that uses your self-hosted pool.
Run basic shell commands (e.g., `uname -a`, `whoami`, `df -h`) to verify that the job executes on your VM.

---

## Success Criteria

* Agent Pool created and visible in Azure DevOps
* Agent registered and running as a service
* Pipeline successfully executed on the self-hosted agent
* Secure connection established using PAT authentication

---


* One challenge you faced while configuring the agent and how you resolved it
* How you would scale this setup to multiple self-hosted agents in production for different application for security. 
