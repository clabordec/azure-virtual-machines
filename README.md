<p align="center">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/174839cb-f9c3-4588-bbd3-2cb6b79d8f8c" />
</p>

<h1>Inspecting Traffic Between Azure Virtual Machines and Adding Firewall Rules</h1>
In this project, we inspect network traffic between Azure Virtual Machines (VMs) and configure firewall rules to allow communication. The process includes creating both Windows and Linux VMs, testing connectivity between them, and troubleshooting blocked traffic using firewall adjustments. Technologies used include Microsoft Azure, PowerShell, MobaXterm, and Remote Desktop Connection. <br />

<h2>Environments and Technologies Used</h2>
- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- MobaXterm
- PowerShell
- Linux CLI

<h2>Operating Systems Used</h2>
- Windows 10 (21H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>
### Create Virtual Machines
- Create a Resource Group.
- Create a Windows 10 Virtual Machine:
  - Assign it to the newly created Resource Group.
  - Create and assign a new Virtual Network (VNet).
- Create a Linux (Ubuntu) Virtual Machine:
  - Assign it to the same Resource Group.
  - Attach it to the same VNet as the Windows VM.
  - Change the authentication type to **Password**.
- Verify connectivity by using each VM’s public IP address via Remote Desktop Connection (RDP) and MobaXterm.

<br />

<h1>Actions and Observations</h1>

## Resource Group Creation
### Create the resource group — this will store all of the necessary resources for the project.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/33771e10-a562-41fa-a620-f67a45f03447" />
</p>
<br />

## Virtual Machine Creation
### Create the `Windows (Windows 10 Pro)` and `Linux (Ubuntu)` Virtual Machines, ensuring both are on the same VNet/subnet.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/71b7d200-5f08-4b6c-ac3e-f6fe7881d14f" />
</p>

<h3>Windows VM</h3>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/2df01268-cde6-4c5f-be2e-77924ce3060c" />
</p>

<h3>Linux VM</h3>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/4e7cce85-f687-47e8-8496-f9adf06f5778" />
</p>
<br />

## Remoting Into the Virtual Machines
### Connect to the Windows VM using the Remote Desktop Connection (RDP) application and the public IP `48.216.217.148`.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/ade5a63d-bbad-40cf-a9c1-78443553a1d9" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/834bf960-551b-4b41-aa6f-6d39f6e29918" />
</p>
<br />

### Once logged in, open PowerShell within the Windows VM and retrieve the private IP address.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/88000cf7-0f50-427c-a44c-0c4897425eb9" />
</p>
<br />

### Connect to the Linux VM using MobaXterm with the public IP `48.216.217.159`.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/2e049777-4c3f-4874-828a-076020e2fe49" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/939ba0a8-cf93-470b-8836-92280711d46f" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/07fbd780-2b7d-4b5d-9415-f01d1e9996ba" />
</p>
<br />

## Testing Connectivity
### From the Windows VM, ping the private IP address assigned to the Linux VM.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/cdb75321-3c33-4f97-8d77-acaa837b9855" />
</p>
<br />

### From the Linux VM, ping the private IP address assigned to the Windows VM.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/465ce3e1-a89a-42c8-b9a9-4917b57ec959" />
</p>

- The Linux VM could not connect to the Windows VM, indicating traffic is being blocked by the Windows Firewall.
- Since the Windows VM is active, the next step is to modify the firewall settings to allow inbound ICMP traffic from the Linux VM.

<br />

## Allow Traffic to Come In
### In the `Windows Defender Firewall with Advanced Security` application, create a new inbound rule allowing traffic from the Linux VM.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/2e233ff1-0536-4f9d-a64a-602eb8097fda" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/c20f872d-4df8-48c4-bc35-7e8780b88708" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/5c14a99b-77e1-460e-aae2-e29de5ef1c0a" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/06549c39-33b3-4ca9-8ef0-3e6a8077fd0f" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/793fe068-d3c3-41fe-9ba0-4f30d2f35ae8" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/da65cabc-5f21-48d4-935f-ffd1844f54a5" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/e1639899-006c-46c7-9771-d86843d04037" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/49b372b2-b6ce-4e4f-8599-2c51dcb07be2" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/8e8bee4e-6099-4c96-b8a5-98bcaf527ce9" />
</p>
<br />

## Re-Test Connectivity
### Ping again from both machines to confirm successful communication between the Windows and Linux VMs.
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/1efb0cdc-0ba8-4f30-bdd3-482f6ae66f30" />
</p>
<p>
<img width="550" height="550" alt="image" src="https://github.com/user-attachments/assets/4f46d613-9032-49e3-8387-056f919433d9" />
</p>

---

<br />

# End of Project
