# Windows Monitoring

Monitor Windows endpoint activity using the Wazuh Agent and verify that
Windows security events are successfully collected and analyzed by Wazuh.

## Monitoring Flow


Windows Endpoint --> Wazuh Agent --> Wazuh Manager -->Wazuh Dashboard

## Windows Security Events

The Wazuh agent collects Windows security events such as:

- Successful logons
- Failed logons
- Logoffs
- User activity
- Security-related events
- Windows Defender configuration events

### Windows Defender configuration events

The Wazuh agent successfully collected Windows endpoint events,
including Microsoft Defender Antivirus and Windows system events.

- Event ID 5007
- Event ID 16384
- Agent IP 192.168.1.39
- Agent name My_Host

<img width="1920" height="942" alt="Screenshot 2026-08-17 122014" src="https://github.com/user-attachments/assets/752b2dff-6ced-4006-bc98-5878d3a70d3f" />

### logons Events(Event ID 4624,4625)

The Wazuh agent successfully collected Windows endpoint events,
including Successful, Failed  logons Events.

<img width="1919" height="841" alt="02-windows-monitoring-events" src="https://github.com/user-attachments/assets/e1a6810b-ab1a-432e-a14b-efb076b4c92e" />

<img width="1919" height="830" alt="07-windows-monitoring-events" src="https://github.com/user-attachments/assets/bddf6836-ab9b-4a96-bec0-e61ef36526e4" />

### Account Modification (Event ID 4738)

Detects changes made to local domain or machine user accounts.

<img width="1917" height="827" alt="Screenshot 2026-08-19 154535" src="https://github.com/user-attachments/assets/1eb08bd2-7d39-4a82-aa74-f197ba8f19d8" />

### Service Installation Detection (Event ID 7045)

Monitors execution of new system services

<img width="1918" height="781" alt="Screenshot 2026-08-19 155345" src="https://github.com/user-attachments/assets/9f2d2642-8169-4b43-9112-7f6074177400" />

### Special Logon Privileges (Event ID 4672)

Fires when sensitive privileges  are assigned to a user logon session.

<img width="1919" height="823" alt="Screenshot 2026-08-19 155120" src="https://github.com/user-attachments/assets/68ddac9b-34e9-4f37-82ff-0f3930735994" />



