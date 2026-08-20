# File Integrity Monitoring (FIM) with Wazuh
Implemented File Integrity Monitoring (FIM) using Wazuh to monitor critical files and directories for unauthorized changes. The lab detects file creation, modification, and deletion events and generates security alerts for investigation.

## * configuration → checking events → understanding the events
### 1. Configure File Integrity Monitoring

I. Open the Wazuh Agent configuration file located at:

       C:\Program Files (x86)\ossec-agent\ossec.conf

II. Open ossec.conf with Notepad as Administrator, Find the File Integrity Monitoring (FIM) section.

III. Locate the <directories> configuration and add the This line 

    <directories realtime="yes" report_changes="yes">Path Of Folder</directories>

<img width="1919" height="839" alt="01-FIM_Wazuh" src="https://github.com/user-attachments/assets/eb5b873b-489c-4ab1-b45c-38981b7c418e" />

 IV.  Save the changes to ossec.conf

--> realtime="yes" enables real-time monitoring of the selected directory.

--> report_changes :- Allows Wazuh to report the actual text changes made inside monitored files, where applicable.

* Avoid monitoring entire root drives such as C:\ or D:\. Also avoid directories containing large numbers of binary files     such as .mp4, .exe, or .zip, as this can generate excessive events and unnecessary resource usage.

### 2. Configure Windows Audit Policies

I.  Press Win + R.

II. Type:

     secpol.msc

III. Press Enter to open Local Security Policy.

<img width="1919" height="609" alt="06-FIM_Wazuh" src="https://github.com/user-attachments/assets/82bccfdb-374a-413b-b853-704b6a2ea553" />

IV. Navigate to:

  Advanced Audit Policy Configuration → System Audit Policies → Object Access

V. Configure Audit File System and enable both Success and Failure.

VI. Also check: Local Policies → Audit Policy → Audit object access

VII. Enable the required auditing options for successful and failed And apply the changes.

### 3. FIM Event Detection

azuh detected file creation, modification, and deletion activities on the monitored Windows endpoint.

<img width="1919" height="830" alt="02-FIM_Wazuh" src="https://github.com/user-attachments/assets/e882cd7f-b93c-41bc-9e36-97d74da932a0" />



