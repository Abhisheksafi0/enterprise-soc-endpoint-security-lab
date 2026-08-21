# Windows File Integrity Monitoring (FIM) With Wazuh
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

## Enable Windows File Auditing for Whodata
To allow Wazuh to identify who performed file operations, enable auditing on the specific folder you want to monitor.
Steps

I. Right-click the folder you want to monitor.

II. Select Properties and Go to Security → Advanced.

III. Open the Auditing tab and Click Add.

IV. Click Select a principal.

V. Enter

-->Everyone

VI. Click Check Names → OK.

VII. Set Applies to: This folder, subfolders and files.

VIII. Under Basic permissions, select the activities you want to audit:
-->Create files, Create folders, Write attributes, Write extended attributes, Delete, Delete subfolders and files,Change permissions, Take ownership

X. Apply → OK.

Note--> Don't apply auditing to the entire C:\ drive. It can generate a very large number of events and increase disk/CPU usage. Use it only on the folder containing the sensitive files you want to demonstrate in your lab

### * Enable Whodata

Whodata provides detailed information about who made a change to a monitored file.

--> When combined with report_changes="yes", Wazuh can also show the specific file content changes, including line-by-line differences.

    <directories whodata="yes" report_changes="yes">Path Of Folder</directories>

<img width="1912" height="786" alt="04-Whodata_FIM" src="https://github.com/user-attachments/assets/842b3d1b-d182-4c52-a69f-2ede2b176463" />

#### * This can provide information such as:

-->Which file changed

-->What type of change occurred

-->Which user/process made the change — Whodata

-->What content was added or removed — report_changes

-->Line-by-line differences where supported

#### * The FIM Whodata evidence includes detailed logs for file creation, modification, and deletion. The screenshots highlight the key event details, while the complete JSON logs are included for reference and verification.

### File Creation

The following event shows a file creation activity, including the
affected file and the user/process responsible for the change.

<img width="1919" height="828" alt="05-Whodata_FIM" src="https://github.com/user-attachments/assets/5cb982d8-bf7d-449d-84d1-79f1a53bf400" />

### File Modification

This event shows a file modification detected by Wazuh FIM.

<img width="1901" height="819" alt="06-Whodata_FIM" src="https://github.com/user-attachments/assets/81eabf18-72f1-4abd-9379-4a9661cad5cb" />

### File Deletion

This event shows a file deletion detected by Wazuh FIM.

<img width="1919" height="817" alt="07-Whodata_FIM" src="https://github.com/user-attachments/assets/fd42f26f-6d19-4713-aa7e-02772e084a34" />

# Ubuntu File Integrity Monitoring (FIM) With Wazuh

I. Configure the Wazuh Agent
Open the Wazuh agent configuration:

    sudo nano /var/ossec/etc/ossec.conf

Go to the <syscheck> XML section and add the directory you want to monitor

    <syscheck>
       <directories realtime="yes" report_changes="yes">/path/to/folder</directories>
    </syscheck>

Replace /path/to/folder with the actual directory you want to monitor.

realtime="yes" — detects changes in real time.

report_changes="yes" — reports the content changes when supported.

II. Install Auditd

Install the Linux auditing service:

    sudo apt-get update
    sudo apt-get install auditd -y

Check that Auditd is running:

    sudo systemctl status auditd

III. Restart the Wazuh Agent

After saving the Wazuh configuration:

    sudo systemctl restart wazuh-agent

* Check the Wazuh dashboard for the resulting file creation, modification, and deletion events.
