<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<br>

<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<br>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- PowerShell
- Linux CLI
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<br>

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<br>

<h2>High-Level Steps</h2>

### Create Virtual Machines
- Create Resource Group
- Create a Windows 10 Virtual Machine
    - Make sure that it is assigned the resource group that was created
    - Make sure that a new Vnet is created and assigned to the following VM
- Create a Linux (Ubuntu) Virtual Machine
    - Make sure that it is assigned the resource group that was created
    - Make sure that it is assigned to the Vnet that was assigned to the Windows VM
    - Change the authentication type to password
- Verify that both VMs work by inputting the public IP address within Remote Desktop Connect(RDP)

<br>

<h2>Actions and Observations</h2>

<p>
![image](https://github.com/user-attachments/assets/2e1fb0e0-eee1-4b12-8050-45dd61a59359)
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="770" alt="image" src="https://github.com/user-attachments/assets/33771e10-a562-41fa-a620-f67a45f03447" />
</p>
<p>
Create the resource group, this resource group will store all of the necessary resources for the project
</p>
<br />

<p>
<img width="959" alt="image" src="https://github.com/user-attachments/assets/71b7d200-5f08-4b6c-ac3e-f6fe7881d14f" />
</p>
<p>
Create the Windows(Windows 10 Pro) Virtual Machnine and the Linux(Ubuntu) Virtual Machnine ensuring that they are both on the same network(Vnet/subnet).
</p>
<p>Windows</p>
<p>
![image](https://github.com/user-attachments/assets/3fb7660a-ea00-471a-bc94-5c43832559b1)
</p>

<h4><b>Linux</b></h4>
<p>
<img width="959" alt="image" src="https://github.com/user-attachments/assets/2df01268-cde6-4c5f-be2e-77924ce3060c" />
</p>
<br />
