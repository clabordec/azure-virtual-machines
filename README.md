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
<img width="600" alt="image" src="https://github.com/user-attachments/assets/71b7d200-5f08-4b6c-ac3e-f6fe7881d14f" />
</p>


<h3>Windows</h3>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/2df01268-cde6-4c5f-be2e-77924ce3060c" />
</p>

<h3>Linux</h3>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/4e7cce85-f687-47e8-8496-f9adf06f5778" />
</p>
<br />

## Remoting Into the Virtual Machines
### Remote into the Windows VM with the public IP address `48.216.217.148` using the Remote Desktop Connection(RDP) application
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/ade5a63d-bbad-40cf-a9c1-78443553a1d9" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/834bf960-551b-4b41-aa6f-6d39f6e29918" />
</p>
<br />

### Once remoted in, open up powershell within the windows VM and get the private IP address
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/88000cf7-0f50-427c-a44c-0c4897425eb9" />
</p>
<br />

### Remote into the Linux VM using the MobaXterm application with the public IP address `48.216.217.159`
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/2e049777-4c3f-4874-828a-076020e2fe49" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/939ba0a8-cf93-470b-8836-92280711d46f" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/07fbd780-2b7d-4b5d-9415-f01d1e9996ba" />
</p>
<br />

## Testing connectivity
### In the Windows VM, ping the private IP address that is assigned to the Linux VM
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/cdb75321-3c33-4f97-8d77-acaa837b9855" />
</p>
<br />

### In the Linux VM, ping the private IP address that is assigned to the Linux VM
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/465ce3e1-a89a-42c8-b9a9-4917b57ec959" />
</p>

- The Linux VM was not able to connect to the Windows VM due to either the server being down or traffic is blocked by the firewall
- Since the server is up, this only leads to the firewall blocking the request from the Linux VM
- I will add a firewall inbound rule to allow requests from the Linux VM

<br />

## Allow Traffic to come in
### Within the `Windows Defender Firewall with Advanced Security` application, create a new rule that will allow traffic from just the Linux machine
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/2e233ff1-0536-4f9d-a64a-602eb8097fda" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/c20f872d-4df8-48c4-bc35-7e8780b88708" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/5c14a99b-77e1-460e-aae2-e29de5ef1c0a" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/06549c39-33b3-4ca9-8ef0-3e6a8077fd0f" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/793fe068-d3c3-41fe-9ba0-4f30d2f35ae8" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/da65cabc-5f21-48d4-935f-ffd1844f54a5" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/e1639899-006c-46c7-9771-d86843d04037" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/49b372b2-b6ce-4e4f-8599-2c51dcb07be2" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/8e8bee4e-6099-4c96-b8a5-98bcaf527ce9" />
</p>
<br />

### Re-test the connectivity between the two VMs
<p>
<img width="435" alt="image" src="https://github.com/user-attachments/assets/1efb0cdc-0ba8-4f30-bdd3-482f6ae66f30" />
</p>
<p>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/4f46d613-9032-49e3-8387-056f919433d9" />
</p>
