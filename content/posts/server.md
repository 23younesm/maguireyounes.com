---
title: "Setting up my Proxmox Server on an HP ProLiant DL380p"
description: "A step-by-step guide to repurposing an HP ProLiant DL380p server with Proxmox and various tools"
date: 2024-07-03
tags: ["Server", "Proxmox", "Virtualization", "Networking"]
---

This post outlines my experience with setting up an HP ProLiant DL380p server to run Proxmox, along with several other tools to enhance its functionality. The aim was to repurpose an older server into a versatile virtualization platform for various projects, including remote access, monitoring, and container management.

## Background

I recently purchased an HP ProLiant DL380p server off Facebook Marketplace. The server's specifications include:

![Server](server.jpg)

- 2 Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz
- 64 GB DDR3 RAM
- HP Ethernet 1Gb 4-port 331FLR Adapter
- 2.2 TB RAID 1 Storage

It was previously running Windows Server 2012 and was used for running VMs with Hyper-V. I decided to switch to Proxmox to leverage its Linux base and robust virtualization capabilities.

## Initial Setup Challenges

### Firmware Update

My first challenge was to boot the server via USB with the [Proxmox installer](https://www.proxmox.com/en/proxmox-virtual-environment/get-started), but the server's firmware was outdated. HP provided an old USB ISO for firmware updates, but it was so outdated that it didn't work. I then turned to the Integrated Lights-Out (ILO) interface for firmware updates.

### Learning ILO

Navigating the ILO interface was a struggle initially. I had to do extensive research to understand its functionalities. Eventually, I managed to update the firmware through the ILO interface, bringing the server up to date. Surprisingly, HP still supports firmware updates for this older server model.

### Installing Proxmox

With the server firmware updated, I used the ILO's virtual DVD feature to mount the Proxmox installer ISO. I successfully installed Proxmox and formatted the disks to my preferences.

## Configuring Proxmox and VMs

### Initial VM Setup

The first thing I did was provision and install a basic Red Hat Linux VM. On this VM, I installed a Cloudflare tunnel, allowing me to securely access my private network from Penn State without the need for port forwarding.

![Network Diagram](network_diagram.png)

### Monitoring and Security

I installed Uptime Kuma, an open-source monitoring service, on the server. Uptime Kuma provides a simple dashboard to monitor various services, including my website, server, tunnel, and SSH access.

{{< github repo="louislam/uptime-kuma" >}}

Additionally, I enhanced security by installing fail2ban on the VMs with SSH access and configuring Proxmox permissions to restrict unauthorized access.

{{< github repo="fail2ban/fail2ban" >}}

### Container Management

To manage Docker containers efficiently, I installed [Portainer](https://www.portainer.io/). This tool allows me to easily spin up and manage containers, such as my Signal API bot.

## Future Plans

With the Proxmox server set up to my liking, I am ready to spin up numerous VMs for practicing red teaming and blue teaming cybersecurity skills. The first test will be during an upcoming Red vs Blue team exercise. I am also looking to learn [Anisble](https://www.ansible.com/) for VM deployments and installing [Wazuh SIEM](https://wazuh.com/) to help monitor for threats. 

## Conclusion

Setting up this server has been a rewarding project, turning an older piece of hardware into a powerful and flexible virtualization platform. The combination of Proxmox, Cloudflare tunnel, Uptime Kuma, and Portainer has provided me with a robust environment for learning and experimentation.

Feel free to follow along with these steps and customize your setup to suit your needs. Happy virtualizing!