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
- Remote Desktop Connection
- MobaXterm
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

<h1>Actions and Observations</h1>

<br />

## Resource Group Creation
### Create the resource group, this resource group will store all of the necessary resources for the project
<p>
<img width="770" alt="image" src="https://github.com/user-attachments/assets/33771e10-a562-41fa-a620-f67a45f03447" />
</p>
<br />

## Virtual Machine Creation
### Create the `Windows(Windows 10 Pro)` Virtual Machine and the `Linux(Ubuntu)` Virtual Machine ensuring that they are both on the same network `(Vnet/subnet)`.
<p>
<img width="959" alt="image" src="https://github.com/user-attachments/assets/71b7d200-5f08-4b6c-ac3e-f6fe7881d14f" />
</p>


<h3>Windows</h3>
<p>
<img width="959" alt="image" src="https://github.com/user-attachments/assets/2df01268-cde6-4c5f-be2e-77924ce3060c" />
</p>

<h3>Linux</h3>
<p>
<img width="959" alt="image" src="https://github.com/user-attachments/assets/4e7cce85-f687-47e8-8496-f9adf06f5778" />
</p>
<br />

## Remoting Into the Virtual Machines
### Remote into the Windows VM with the public IP address `48.216.217.148` using the Remote Desktop Connection(RDP) application
<p>
<img width="944" alt="image" src="https://github.com/user-attachments/assets/ade5a63d-bbad-40cf-a9c1-78443553a1d9" />
</p>
<p>
<img width="302" alt="image" src="https://github.com/user-attachments/assets/834bf960-551b-4b41-aa6f-6d39f6e29918" />
</p>
<br />

### Once remoted in, open up powershell within the windows VM and get the private IP address
<p>
<img width="959" alt="image" src="https://github.com/user-attachments/assets/88000cf7-0f50-427c-a44c-0c4897425eb9" />
</p>
<br />

### Remote into the Linux VM using the MobaXterm application
<p>
<img width="935" alt="image" src="https://github.com/user-attachments/assets/2e049777-4c3f-4874-828a-076020e2fe49" />
</p>
<p>
<img width="638" alt="image" src="https://github.com/user-attachments/assets/939ba0a8-cf93-470b-8836-92280711d46f" />
</p>
<p>
<img width="536" alt="image" src="https://github.com/user-attachments/assets/07fbd780-2b7d-4b5d-9415-f01d1e9996ba" />
</p>
<br />
