# Azure Compute and Networking Lab

## Overview

This lab focuses on creating virtual machines in Azure and analyzing their network traffic using Wireshark. The first portion of the lab involves creating and provisioning resources. The second portion of the lab involves performing activities on the network. The third and final portion of the lab involves cleanup. 

### Create and Provision Resources
* Create resource group in Azure
* Create Windows 10 Professional virtual machine in Azure
* Create Ubuntu virtual machine in Azure
* Examine virtual network topology in Azure

### Perform Activities on the Network
* Observe ICMP traffic using WireShark
* Observe SSH traffic using WireShark
* Observe DHCP traffic using WireShark
* Observe DNS traffic using WireShark

### Lab Cleanup
* Close connections
* Delete resource groups

## Environments and Technologies Used
* Microsoft Azure 
* Remote Desktop Connection
* Various command line tools (e.g., `ping`, `ssh`, `ipconfig`, and `nslookup`)
* Various network protocols (e.g., ICMP, SSH, DHCP, and DNS)
* Network security groups 
* Wireshark

## Operating Systems Used
* Windows 10 Professional 
* Ubuntu Server 20.04

## Create and Provision Resources

### Create Resource Group in Azure 

> ![image](https://user-images.githubusercontent.com/15792522/200154000-f201fe1c-bfab-4ed0-b886-b5206b508298.png)

### Create Windows 10 Professional Virtual Machine in Azure

### Initial Configuration

> ![image](https://user-images.githubusercontent.com/15792522/200154220-6e8077bb-f385-488b-aab7-20a1c6b6dc99.png)

> ![image](https://user-images.githubusercontent.com/15792522/200154236-624b0a3f-e620-4437-a5ee-16f3baa71e19.png)

### Disk Configuration

> ![image](https://user-images.githubusercontent.com/15792522/200154286-9da316fb-9b5d-4a53-879c-b32c4fba34ca.png)

### Networking Configuration

> ![image](https://user-images.githubusercontent.com/15792522/200154357-742319b8-51c2-4fe2-85af-8e4d5798683d.png)

### Create Ubuntu Server 20.04 Virtual Machine in Azure

### Initial Configuration

> ![image](https://user-images.githubusercontent.com/15792522/200154542-f9f886a4-2cf8-470a-90ed-89536a1c0b38.png)

> ![image](https://user-images.githubusercontent.com/15792522/200154561-24ab3000-a670-40e9-8c9d-2688955a1401.png)

### Disk Configuration

> ![image](https://user-images.githubusercontent.com/15792522/200154595-4f134817-f55e-498b-bbaf-e50eb4a9e746.png)

### Networking Configuration

> ![image](https://user-images.githubusercontent.com/15792522/200154610-d962cb83-5511-457f-9518-a097af73b40c.png)

### Examine Virtual Network Topology 

This is an overview of the network topology that was created, as seen from the **Network Watcher** screen.

> ![image](https://user-images.githubusercontent.com/15792522/200154702-c5e49395-33fd-492a-b987-2af2791d9067.png)

## Peform Activities on Network

### Observe ICMP Traffic Using WireShark

Use **Remote Desktop Connection** to connect to the Windows 10 virtual machine using its public IP address.

> ![image](https://user-images.githubusercontent.com/15792522/200155017-9b46c10c-1741-4bd0-9efa-a2b913de489a.png)

> ![image](https://user-images.githubusercontent.com/15792522/200155045-1e84cd97-cb37-44e1-ba24-f4075c7e867a.png)

> ![image](https://user-images.githubusercontent.com/15792522/200155092-d9360a70-8f4a-4ea1-b2d7-0c3184cd1c9d.png)

Install **WireShark** on the Windows 10 virtual machine (https://www.wireshark.org/#download). 

> ![image](https://user-images.githubusercontent.com/15792522/200155266-b079949b-4e5c-46a6-8ad0-54583ae3069c.png)

Open **WireShark** and begin analyzing Ethernet traffic. 

> ![image](https://user-images.githubusercontent.com/15792522/200155366-61fc7e7b-f571-4859-b6f7-aea05c3105c5.png)

Locate the private IP address of the Ubuntu virtual machine. 

> ![image](https://user-images.githubusercontent.com/15792522/200155441-5e2cc981-0fd2-4b23-ab90-4303c430551d.png)

Open **PowerShell** on the Windows 10 virtual machine and use it to ping the Ubuntu virtual machine.

> ![image](https://user-images.githubusercontent.com/15792522/200155502-53666bdf-9897-4587-a8e5-51b550c6ee3b.png)

Filter ICMP traffic in **WireShark**. 

> ![image](https://user-images.githubusercontent.com/15792522/200155556-de25718e-a55a-4ea6-9a80-9b5f9b609796.png)

Begin a perpetual ping from the Windows 10 virtual machine to the Ubuntu virtual machine, then configure the Ubuntu virtual machine's firewall to block ICMP traffic.

> ![image](https://user-images.githubusercontent.com/15792522/200156133-ef9c8665-abb5-4a04-bdc4-5b07eb6ec3f6.png)

Create a new inbound security rule in the Ubuntu virtual machine's **Network Security Group** that blocks ICMP traffic from anywhere. 

> ![image](https://user-images.githubusercontent.com/15792522/200155965-5f482538-76f0-4400-9e79-c872863fa2d8.png)

Observe the requests timing out. 

> ![image](https://user-images.githubusercontent.com/15792522/200156077-a0750076-d78e-4186-89f4-8854e313b3ea.png)

Observe that no response is found. 

> ![image](https://user-images.githubusercontent.com/15792522/200156222-88f91d7f-42aa-4306-9ed7-30e0504f6bdc.png)

### Observe SSH Traffic Using WireShark

Connect to the Ubuntu virtual machine from the Windows 10 virtual machine via SSH using **PowerShell**. 

> ![image](https://user-images.githubusercontent.com/15792522/200156443-73a47359-4b9c-445e-9398-d09fc96edc71.png)

Filter SSH traffic in **WireShark**.

> ![image](https://user-images.githubusercontent.com/15792522/200156488-59e92d34-594e-49b7-a4f5-dd2949ac0712.png)

### Observe DHCP Traffic Using WireShark

Enter `ipconfig /renew` in **PowerShell** to generate DHCP traffic.

> ![image](https://user-images.githubusercontent.com/15792522/200156656-c1218834-23a8-4abc-bf4f-ae4cc6651a21.png)

Filter DHCP traffic in **WireShark**. 

> ![image](https://user-images.githubusercontent.com/15792522/200156676-0d300e23-5485-4b81-a68d-51a85a849498.png)

### Observe DNS Traffic Using WireShark

Filter DNS traffic in **WireShark**.

> ![image](https://user-images.githubusercontent.com/15792522/200156766-7ebc6c9d-2681-4a37-9a88-180486ebaba6.png)

Enter `nslookup google.com` in **PowerShell** to generate new DNS traffic. 

> ![image](https://user-images.githubusercontent.com/15792522/200156868-a7b5e606-830e-4014-8da2-1653103a619a.png)

> ![image](https://user-images.githubusercontent.com/15792522/200156886-05af3785-6fef-4248-8be0-f4305be690a8.png)

## Lab Cleanup 

Close connections and delete resource groups when done using them to avoid incurring unnecessary costs.
