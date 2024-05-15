# Honeypot Setup with T-Pot

This repository provides step-by-step instructions to build and deploy a honeypot using T-Pot on a cloud provider. T-Pot is an all-in-one multi-honeypot platform that includes various visualization options and supports over 20 honeypots.

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Setup Instructions](#setup-instructions)
    1. [Create Cloud Provider Account](#create-cloud-provider-account)
    2. [Deploy New Server](#deploy-new-server)
    3. [Upload T-Pot ISO](#upload-t-pot-iso)
    4. [Create Firewall Group](#create-firewall-group)
    5. [Configure T-Pot](#configure-t-pot)
    6. [Accessing the Honeypot](#accessing-the-honeypot)
    7. [Enable Public Access](#enable-public-access)
4. [Next Steps](#next-steps)
5. [References](#references)

## Introduction

A honeypot is a system designed to attract and detect unauthorized activity. It can be useful for learning more about attackers and distracting them. This guide will help you set up a collection of honeypots using T-Pot on a cloud provider, specifically Vulture, though any cloud provider can be used.

## Prerequisites

- A computer with internet access
- Basic knowledge of cloud providers and Linux command line

## Setup Instructions

### 1. Create Cloud Provider Account

1. Sign up for a cloud provider account. This guide uses Vulture, but you can use any provider.
2. Use the [Vulture sign-up link](https://www.vultr.com/) to get a free $100 credit.

### 2. Deploy New Server

1. Log in to your cloud provider account.
2. Click on the "Deploy" button and select "Deploy New Server."
3. Choose "Cloud Compute" and "Shared CPU" for cost efficiency.
4. Select the location closest to you.
5. Under "Choose Image," select "Upload ISO."
6. Upload the T-Pot ISO (link provided below).

### 3. Upload T-Pot ISO

1. Copy the T-Pot ISO URL from the [T-Pot GitHub repository](https://github.com/dtag-dev-sec/tpotce).
2. Paste the URL in the "Upload ISO" section and click "Upload."
3. After the upload, select the uploaded T-Pot ISO for your server.

### 4. Create Firewall Group

1. While the server is deploying, navigate to the "Firewall" section under "Settings."
2. Click "Manage" and then "Add Firewall Group."
3. Name the group "Honeypot" and add the following rules:
    - **TCP**: Port range 1-65535, source "My IP."
    - **UDP**: Port range 1-65535, source "My IP."
4. Save the firewall group.

### 5. Configure T-Pot

1. Once the server status is "Running," click on "View Console."
2. Follow the on-screen instructions to complete the T-Pot setup:
    - Select your location and keyboard layout.
    - Choose "Standard" edition.
    - Set the username (default is `tc`) and password.
    - Complete the setup.

### 6. Accessing the Honeypot

1. Note the IP addresses and ports provided at the end of the setup:
    - SSH access.
    - Web interface.
    - Admin portal.
2. Access the T-Pot web interface using the provided IP and port with HTTPS:
    ```plaintext
    https://<your-ip>:<web-port>
    ```
3. Log in using the username and password you set during setup.

### 7. Enable Public Access

1. Go back to the "Firewall" section and remove the initial rules allowing only your IP.
2. Create new rules to allow public access:
    - **TCP**: Port range 1-65535, source "Anywhere."
    - **UDP**: Port range 1-65535, source "Anywhere."
3. Save the new firewall rules.

## Next Steps

1. Explore the T-Pot web interface:
    - **Attack Map**: Visualize incoming attacks in real-time.
    - **Kibana**: Query data and create visualizations.
2. Practice creating queries and analyzing data in Kibana.
3. Leave the honeypot running to collect data over time and review the collected data for insights.

## References

- [T-Pot GitHub Repository](https://github.com/dtag-dev-sec/tpotce)
- [Vulture Cloud Provider](https://www.vultr.com/)
