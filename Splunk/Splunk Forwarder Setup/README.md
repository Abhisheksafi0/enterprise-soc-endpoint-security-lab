# * Installing Forwarder Deployment on Windows 
Installing the Splunk Universal Forwarder on Windows endpoints to securely collect and send system logs to the Splunk Server for centralized monitoring and analysis.

--> Note:- Linux Forwarder Installation ⬇️

## describe all installation in the all steps        

### Step 1 :-

irst, download the Splunk Universal Forwarder from the Splunk platform. Forwarder installers are available for different operating systems. Here, we choose Windows.

<img width="1907" height="829" alt="Screenshot 2026-08-14 173607" src="https://github.com/user-attachments/assets/254d96b8-749d-43eb-8c77-4f3394bc2b5c" />

<img width="1904" height="832" alt="Screenshot 2026-08-14 173647" src="https://github.com/user-attachments/assets/e57d8379-f065-46d5-8a9d-54e101c3e2c1" />

### step 2:-

Transfer the downloaded file to the Windows Agent PC where you want to install and monitor it. Then, start the installation process.

<img width="878" height="616" alt="WhatsApp Image 2026-08-15 at 11 00 35" src="https://github.com/user-attachments/assets/21349662-c543-4d75-8f99-dc25e36dca5b" />

Select the optimization option, choose “Local System,” and check all the available boxes.

<img width="824" height="598" alt="WhatsApp Image 2026-08-15 at 11 00 35 (1)" src="https://github.com/user-attachments/assets/49d38547-625b-4db5-b36a-6424243079d6" />

<img width="851" height="613" alt="WhatsApp Image 2026-08-15 at 11 00 35 (2)" src="https://github.com/user-attachments/assets/8859fd29-1e9a-4316-a42c-125f25897b84" />

Create the credentials by setting a username and password.

<img width="839" height="594" alt="WhatsApp Image 2026-08-15 at 11 00 35 (3)" src="https://github.com/user-attachments/assets/d7cc268b-8d03-4bef-b6ca-296fa3b9aea6" />

Setup the Deployment Server( use default port).

<img width="788" height="598" alt="WhatsApp Image 2026-08-15 at 11 00 35 (4)" src="https://github.com/user-attachments/assets/d2dfde84-6468-4a3f-86b0-3b86e830529a" />

Set Up the Receiving Indexer( you can setup same IP, set the port).

<img width="885" height="587" alt="WhatsApp Image 2026-08-15 at 11 00 36" src="https://github.com/user-attachments/assets/c2256ce8-45c9-4661-b2cd-d61fd8100549" />

There, you will see the “Install” option. Click it and wait for the installation to finish.

<img width="790" height="591" alt="WhatsApp Image 2026-08-15 at 11 00 36 (1)" src="https://github.com/user-attachments/assets/9eb2c846-7dda-45d3-996d-0d3342d2ad7e" />

<img width="828" height="608" alt="WhatsApp Image 2026-08-15 at 11 00 36 (2)" src="https://github.com/user-attachments/assets/2d98675b-02c6-4d79-b44a-67e27ef586ed" />

### Step 3:-

Go to the Splunk Server Dashboard, open “Settings,” and click “Forwarding and Receiving.”

<img width="1912" height="803" alt="Screenshot 2026-08-15 121949" src="https://github.com/user-attachments/assets/62e73c43-b6f6-462a-a0a1-2ddf15868612" />

<img width="1890" height="799" alt="Screenshot 2026-08-15 122002" src="https://github.com/user-attachments/assets/11825de9-ada8-43b1-97eb-0624c3018d61" />

Add the port number that you configured earlier for the Receiving Indexer.

<img width="1919" height="395" alt="Screenshot 2026-08-15 122035" src="https://github.com/user-attachments/assets/72814e23-a8d2-4840-b557-c30d757bfc27" />

There, you will see your Forwarder device listed in the “Data Summary” section.

<img width="1912" height="822" alt="Screenshot 2026-08-14 201448" src="https://github.com/user-attachments/assets/5d787208-2954-417e-80a5-282e07fb54a7" />

<img width="1204" height="673" alt="Screenshot 2026-08-15 110001" src="https://github.com/user-attachments/assets/96a6fec0-046e-4be5-adaf-aa7b1e9d9f44" />

# * Splunk Universal Forwarder on Linux.

### Step 1:
Download & Install

<img width="1326" height="568" alt="Screenshot 2026-08-16 003205" src="https://github.com/user-attachments/assets/0a6367a9-7433-45f4-9af2-99378bf52c83" />


    wget -O splunkforwarder-10.4.2-33c3bf42cd73-linux-amd64.deb "https://download.splunk.com/products/universalforwarder/releases/10.4.2/linux/splunkforwarder-10.4.2-33c3bf42cd73-linux-amd64.deb"

### Step 2:-

Accept license and set admin credentials.

<img width="1511" height="801" alt="Screenshot 2026-08-16 010518" src="https://github.com/user-attachments/assets/6c801b86-1a20-49e7-b55c-cf57deb01b2a" />


    sudo /opt/splunkforwarder/bin/splunk start --accept-license

Disable Boot-Start.

    sudo /opt/splunkforwarder/bin/splunk disable boot-start

Enable Boot-Start

<img width="1348" height="315" alt="Screenshot 2026-08-16 010933" src="https://github.com/user-attachments/assets/4189561c-c1f5-4641-8c8e-5ce4e7f8d192" />

    sudo /opt/splunkforwarder/bin/splunk enable boot-start -systemd-managed 1

### Step 3:-
Add the Splunk Indexer Target.
Note: Replace <INDEXER_IP> with the actual IP address of your Splunk Indexer.

<img width="1358" height="277" alt="Screenshot 2026-08-16 010711" src="https://github.com/user-attachments/assets/ee8a9276-0f76-48e3-b961-0230f846e2d0" />


    sudo /opt/splunkforwarder/bin/splunk add forward-server <INDEXER_IP>:9997

Add log file monitors.

    sudo /opt/splunkforwarder/bin/splunk add monitor /var/log/syslog -index main
    sudo /opt/splunkforwarder/bin/splunk add monitor /var/log/auth.log -index main

Restart the Splunk Forwarder.

    sudo systemctl restart SplunkForwarder

Check status.

    sudo systemctl status SplunkForwarder

  Check the Splunk Indexer Web UI to verify that the Linux Forwarder is connected and sending data successfully.

  <img width="1911" height="809" alt="Screenshot 2026-08-16 011938" src="https://github.com/user-attachments/assets/6e688643-a342-4c98-b8ad-9acf397ca9a6" />
