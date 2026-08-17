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














