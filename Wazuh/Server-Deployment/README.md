# 🛡️ Wazuh Server Deployment

This repository provides a comprehensive, step-by-step guide to deploying and configuring a Wazuh Server on Ubuntu 22.04 LTS.
The guide covers the complete setup process, from preparing the Ubuntu server and configuring the environment to installing Wazuh components and verifying the Wazuh Dashboard.


---

## Step-by-Step Guide: Wazuh Server Deployment

### 1. Set Up Ubuntu 22.04

Download the **Ubuntu 22.04 LTS Server ISO** from the official Ubuntu website:

[Ubuntu 22.04 Server — Official Download](https://ubuntu.com/download/server)

The Ubuntu server will be deployed as a virtual machine using **Oracle VirtualBox**.

---

### 2. Check System Requirements

Before creating the virtual machine, make sure your system meets the basic requirements:

* 64-bit processor
* Hardware virtualization enabled in BIOS/UEFI
* Oracle VirtualBox, VMware, or another supported virtualization platform

#### Recommended Wazuh Lab VM Configuration

| Resource         |           Configuration |
| ---------------- | ----------------------: |
| CPU              |                 4 cores |
| RAM              |                    8 GB |
| Storage          |                   50 GB |
| Operating System | Ubuntu Server 22.04 LTS |


### 3. Create the Ubuntu Virtual Machine

Open **Oracle VirtualBox** and create a new virtual machine.

Select:

* **Type:** Linux
* **Version:** Ubuntu (64-bit)
* **ISO Image:** Ubuntu Server 22.04 LTS ISO

#### Virtual Machine Configuration

The VM is configured with:

* **CPU:** 4 cores
* **RAM:** 8 GB
* **Storage:** 50 GB

![Virtual Machine Configuration](https://github.com/user-attachments/assets/47683f94-1417-4a92-b5d0-780457505f7b)

---

### 4. Configure Hardware

Configure the virtual machine hardware according to the requirements above.

* CPU: 4 cores
* Memory: 8 GB
* Virtual Disk: 50 GB

![Hardware Configuration](https://github.com/user-attachments/assets/fedd3aca-baf0-4f68-9fda-03a0a247beec)

---

### 5. Configure Network

Configure the virtual network adapter so that the Ubuntu server can communicate with the other systems in the lab.

The network mode should be selected according to your lab topology.

![Network Configuration](https://github.com/user-attachments/assets/b507d6b7-7b89-4cef-abc3-4a704098a0b0)

---

### 6. Check All Setting.
This is fulfill the requirement

![Ubuntu Server VM Configuration](https://github.com/user-attachments/assets/39f97df9-c146-4001-88ac-b35abe358156)

---

### 7. Start the Virtual Machine

Start the newly created Ubuntu Server virtual machine.

![Start Ubuntu Server VM](https://github.com/user-attachments/assets/ea79c5df-8d81-4bd0-9b6e-4055a3fbd118)

### 8. Select your Language.

<img width="1417" height="478" alt="Ubuntu-End png" src="https://github.com/user-attachments/assets/21157775-cc28-4133-abdd-a220ba3a73ce" />

### 9. SHH setup.

<img width="1459" height="858" alt="Ubuntu-ssh png" src="https://github.com/user-attachments/assets/ef5db990-b878-4a91-a881-e5b069a53d70" />

### 10. Ubuntu installation Done.

<img width="1471" height="861" alt="Ubuntu-reboot png" src="https://github.com/user-attachments/assets/35814122-ee04-4a64-bad4-0829293458ce" />

### 11.Log into your Ubuntu VM and run:
Update And Upgrade First.
 
    sudo apt update && sudo apt upgrade -y
    
Download and run the Wazuh installation assistant.

     curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

Wait approximately 15–20 minutes, Once the process finishes, you should see a message confirming that the Wazuh installation was completed successfully.
your credentials:

Username: admin

Password: <ADMIN_PASSWORD>

<img width="980" height="686" alt="Screenshot 2026-08-07 141913" src="https://github.com/user-attachments/assets/286c06ec-77c9-43ac-8aff-49798ead9b56" />

* Change the Wazuh Dashboard admin password.

      sudo /usr/share/wazuh-indexer/plugins/opensearch-security/tools/wazuh-passwords-tool.sh -u admin -p 'YourNewPassword'
  Use special characters for password.(.  *  +  ?  -)

  ## 11. Open the server IP on browser.
  <img width="1916" height="1014" alt="Screenshot 2026-08-13 100648" src="https://github.com/user-attachments/assets/f4ce4cbc-6def-4e7f-864c-82609a6aa2cd" />

Now you are there Wazuh Dashboard.
<img width="1912" height="1017" alt="Screenshot 2026-08-13 100737" src="https://github.com/user-attachments/assets/6ce9f910-0834-4b8b-9b93-b2ed033df22d" />
