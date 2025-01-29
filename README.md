# MALWARE ANALYSIS LAB

## Objective
[Brief Objective - Remove this afterwards]

The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Requirements

- Hypervisor - Vmware, Virtualbox or Hyper-V (Will be using VMware for this demonstration).
- Operating Sysytem - Windows 10 x64 (Installed on your hypervisor)
- Memory - Minimum 80gig
- Installed memory - 2gig ram Minimum
- System type - 64-bit Operating System
- FLARE VM - Windows malware analysis distribution with all the tools we need for malware analysis.

### Security Guidlines

- When executing malware ensure your network configuration is set to host-only
- Do not plug any usb devices in to the VM
- Make sure you download compressed and password protected samples to avoid accidental execution.
- Keep Hypervisor updated
- Do not store any valuable data on your analysis VM
- Disable shared folders, before executing or analizing
- Take snapshots before executing any sample

## Steps
drag & drop screenshots here or use imgur and reference them using imgsrc

### 1. Download FLARE VM

- Click here to download FLARE VM from the GitHub Repository
![2025-01-29 14_48_03-GitHub - mandiant_flare-vm_ A collection of software installations scripts for W](https://github.com/user-attachments/assets/ccd42f3a-d9ee-49c5-a4a1-67e6e57ac724)

  *Ref 1: FLARE VM Repository*

## Note:
I strongly recommend using Flare VM within a virtualized environment for malware analysis to protect and isolate your physical device and network from malicious activities

I assume you already know how to set up and configure a virtualized environment. Start by creating a new virtual machine (VM) and performing a fresh installation of Windows. Flare VM is designed for Windows 7 SP1 or newer, so choose a version that best suits your needs (in this guide, I will be using Windows 10 Pro).

From this point forward, all installation steps should be performed within your VM to ensure a secure and controlled environment.

- At this point, you should take a snapshot of your machine before proceeding.


### 2. Disable Windows Defender and Pause windows update:

- Use Windows + R key to open the "Run" terminal
- Type in "regedit" to open "Registry Editor"

![2025-01-29 16_58_42-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/3af60302-b53a-4f34-bcbd-c34970d1c519)

  *Ref 2: Run Window*

- Navigate to \HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender

![2025-01-29 17_01_34-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/abc2fa4b-8930-41b1-83af-1d313ff38724)

  *Ref 3: Registry Editor 1*

- Right click on "Windows Defender" then "New" and then "DWORD (32-bit) Value". Rename the value "DisableAntiSpyware"

![2025-01-29 17_03_54-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/e3610395-27c8-407a-86fa-e6c2960ebb36)

  *Ref 4: Registry Editor 2*

![2025-01-29 17_08_18-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/da6a7956-3272-4dbe-aec9-6d5cab7431bd)

  *Ref 5: Registry Editor 3*

- Double click on the "DisableAntiSpyware", a new window will open and on the "value date" change the value for "0" to "1"

![2025-01-29 17_10_28-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/5afe710a-ae16-4d5c-84e4-60d3fc9c77f9)

  *Ref 6: Edit DWORD (32-bit) popup*

- Click "OK" and exit "regedit"

- You can delete the "DisableAntiSpyware" or change it's value from "1" to "0" to reactivate your Windows Defender.


- Now we need to disable updates on your machine
- Press the "windows" button and search for "Check for Updates"

![2025-01-29 18_07_01-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/0a09de2f-0337-4d87-b723-e1ec488cc3b5)

  *Ref 7: Windows tab*

- Select "Pause updates for 7 days"

![Image](https://github.com/user-attachments/assets/8af4afb5-2dfa-4973-8888-2c612615b158)

  *Ref 8: Windows Update tab*
  
- Restart your machine after this.


### 3. Install FLARE VM

- Extract the FLARE VM repository you just downloaded to a directory of your choice (mine is on the Desktop).
- Run PowerShell as an administrator, as elevated privileges are required for installation.

![2025-01-29 15_11_47-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/560afa71-2dc4-42ad-b1b8-dcacb8f9ccaa)

  *Ref 9: Windows tab*

- In PowerShell, navigate to the directory where you extracted the FLARE VM repository.
- Enable the unrestricted execution policy for PowerShell by running the following command:
 *Set-ExecutionPolicy Unrestricted*
- When prompted by PowerShell, respond with 'Y' or 'A' to confirm 'Yes to All'.


![2025-01-29 17_49_45-Windows 10 x64-Flare - VMware Workstation](https://github.com/user-attachments/assets/cbe00560-c7e3-4a8c-8366-dc4858b1e5d5)

  *Ref 10: Windows PowerShell*

  
