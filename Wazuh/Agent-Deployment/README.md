# Installing Wazuh Agents on Windows Endpoints

Installing the Wazuh Agent on Windows endpoints to collect logs and monitor security activity.
The agent connects to the Wazuh Server for centralized monitoring and security analysis.
It helps detect suspicious activity and generate security alerts for investigation.


## describe all installation in the all steps

### Step 1 :-
The first step should be generating the Windows Agent download and installation command from the Wazuh Server/Dashboard.
In Agent Summary, click “Deploy New Agent.” You will then see an interface like the one shown below.
<img width="1918" height="844" alt="Screenshot 2026-08-13 100937" src="https://github.com/user-attachments/assets/3289b07b-db5b-4dda-9d72-b06026a8d55b" />
<img width="1914" height="845" alt="Screenshot 2026-08-13 100954" src="https://github.com/user-attachments/assets/e93ea0a2-16ca-451b-b210-202f44501c38" />
### Step 2:-
--> Select the Operating System: Choose Windows.

--> Assign the Server Address: Enter the Wazuh Server IP address.

--> Assign an Agent Name: Enter a unique name for the Windows endpoint.

--> Select the Agent Group: Choose the Default group.

### Steps 3:-

Run the following command in PowerShell on the Windows Agent PC to download, install

    Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.14.7-1.msi -OutFile $env:tmp\wazuh-agent; msiexec.exe /i $env:tmp\wazuh-agent /q WAZUH_MANAGER='192.168.1.37' WAZUH_AGENT_GROUP='default' WAZUH_AGENT_NAME='Vishal_PC'


  <img width="1600" height="900" alt="WhatsApp Image 2026-08-13 at 22 47 50" src="https://github.com/user-attachments/assets/8d38b545-a4f9-41ff-a6ca-c6322085e4dd" />

  Start the Wazuh Agent.

    NET START Wazuh
