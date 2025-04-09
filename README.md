# SIEM-Splunk-Project

# 🛡️ Splunk SIEM Project

This project demonstrates a complete setup of **Splunk Enterprise** and **Splunk Universal Forwarder** in a home lab using **Ubuntu Server** and **Ubuntu ISO** machines. It includes installation, log forwarding, real-time monitoring, and dashboard visualizations.

---

## 🧰 Tools Used

- **Ubuntu Server (for Splunk Enterprise)**
- **Ubuntu ISO Desktop (for Universal Forwarder)**
- **Splunk Enterprise (Free Edition)**
- **Splunk Universal Forwarder**
- **VMware Workstation**

---

## 1️⃣ Install Splunk Enterprise & Splunk Forwarder (Ubuntu Server)

- ### Register or log in to [splunk.com](https://splunk.com)
- ### Download the `.deb` files for** **Splunk Enterprise** and **Splunk Universal Forwarder**

![image](https://github.com/user-attachments/assets/436fa64a-d5d4-4bba-b98c-4bc72c4fa29a)
![image](https://github.com/user-attachments/assets/e3246ae3-cd6a-41b3-8c0c-1cf4147c0307)
![image](https://github.com/user-attachments/assets/bc7030c2-a820-478a-b178-829b3a3b768a)
![image](https://github.com/user-attachments/assets/57f05e7e-93f6-4f12-accd-4ac5fb936278)
![image](https://github.com/user-attachments/assets/2be555fe-ebe1-464f-8b7c-36d17ef49bef)

- ### Use Python3 HTTP server to transfer the forwarder package: python3 -m http.server

- ### Open Firefox in the Ubuntu ISO machine, enter the IP address of the server (with port 8000) and download the Splunk Universal Forwarder.

![image](https://github.com/user-attachments/assets/6e00cdf9-0129-4833-ba36-11538ac9a752)
![image](https://github.com/user-attachments/assets/868be4df-52c5-41d2-aa5d-7f5f51f1245e)

- ### Set up Splunk Enterprise on Ubuntu Server:

![image](https://github.com/user-attachments/assets/0f49cfbc-80f5-4733-876b-ed388d2fa661)
![image](https://github.com/user-attachments/assets/e370b2b8-b6ce-4acd-a12e-ae2fabdbec5c)
![image](https://github.com/user-attachments/assets/9cda0ee8-79aa-47cf-918f-fe91cc97a702)
![image](https://github.com/user-attachments/assets/4cffb4a0-f4ec-4e59-a42f-141e65167cf4)
![image](https://github.com/user-attachments/assets/8c9168e9-9b0d-4f60-8776-f52723c14df0)
![image](https://github.com/user-attachments/assets/2a119bf4-c99d-4023-b9f1-529a2346e479)
![image](https://github.com/user-attachments/assets/98389e51-a0ed-4b8b-8244-17bfd2b98baf)

- ### Start Splunk:```sudo /opt/splunk/bin/splunk start```

![image](https://github.com/user-attachments/assets/abdaaed3-fb13-4461-9d64-04bc1572814e)
![image](https://github.com/user-attachments/assets/c1a24f96-92e7-413c-8886-263c94bab34c)
![image](https://github.com/user-attachments/assets/22970daf-7beb-471c-856d-1ea705da54af)
![image](https://github.com/user-attachments/assets/a2b28746-fb70-4f79-a449-0afcdf653360)

- ### Access Splunk Web at: http://<server-ip>:8000

![image](https://github.com/user-attachments/assets/40a6191f-c417-42df-8e30-975e01b7f551)
![image](https://github.com/user-attachments/assets/56fe23ea-1664-4c07-a21b-e1e8a07a634b)

- ### ⚙️ Set Up Port 9997 for Receiving Logs

- ### Go to Settings > Forwarding and receiving > Configure receiving

- ### Create a new receiving port: 9997
![image](https://github.com/user-attachments/assets/6985670e-9ac9-4705-a136-7fd4108f2d2f)
![image](https://github.com/user-attachments/assets/1efb6f3d-441b-4c8b-855f-5accb473c34d)
![image](https://github.com/user-attachments/assets/579fdf83-5de0-44ac-ab59-08fd6222e2e7)
![image](https://github.com/user-attachments/assets/6e4a803d-4b1b-45b6-9f5e-adc00dc1e0bd)
![image](https://github.com/user-attachments/assets/350199af-dbb8-4f43-93c1-2b691b95719a)

## 2️⃣ Install Splunk Universal Forwarder (Ubuntu ISO)

- ### Open terminal and navigate to Downloads:```sudo dpkg -i splunkforwarder-9.4.1-e3bdab23ac8-linux-amd64.deb```
![image](https://github.com/user-attachments/assets/724d4afb-80cc-4f84-a96f-ed446278f666)
- ### Fix permissions:```sudo chown -R splunkfwd:splunkfwd /opt/splunkforwarder/```
![image](https://github.com/user-attachments/assets/9383b066-ee79-42f1-b00f-6f3525a22731)
![image](https://github.com/user-attachments/assets/28ea6ed1-d41b-4b6b-b5ed-9029d587d0ad)
![image](https://github.com/user-attachments/assets/3d90eabf-b834-44e2-a9e8-006faf17ee1c)
- ### Start the forwarder:```sudo ./splunk start --accept-license```
![image](https://github.com/user-attachments/assets/4d128920-80e7-4b78-ae08-933754f6b0ba)
![image](https://github.com/user-attachments/assets/e3689b96-0126-48bf-9238-f09982823815)

### 🔁 Forward Logs to Splunk Server

- ### Add the Splunk Server IP and port: ```./splunk add forward-server 192.168.235.128:9997```

- ### Confirm with:```./splunk list forward-server```

- ### Expected Output: Active forwards: 192.168.235.128:9997
                      

![image](https://github.com/user-attachments/assets/cca5961a-2b07-49bf-9cf6-2a1e0eced4fa)
![image](https://github.com/user-attachments/assets/901be5b7-b190-4eec-9ccb-377f718479d6)

- ### Start forwarder:```sudo /opt/splunkforwarder/bin/splunk start```
![image](https://github.com/user-attachments/assets/1cf8c600-d9b1-406e-935a-abc9e04bd8a6)

### ✅ Validate Log Forwarding

- ### Go to Splunk Web UI

- ### Navigate to: Search & Reporting > Data Summary > Hosts

- ### Confirm logs are received from the Ubuntu ISO client

![image](https://github.com/user-attachments/assets/d17a083a-72ec-4831-8657-fb92a09a43b6)
![image](https://github.com/user-attachments/assets/b5d681d2-5600-439c-9534-8027485a7b60)
![image](https://github.com/user-attachments/assets/50fa14d6-f838-4b99-b0ae-a29cead152e3)
![image](https://github.com/user-attachments/assets/3cace987-292d-4233-8dd9-837a834f1429)

### 📊 Dashboard & Visualization

- ### Real-time dashboard created to monitor logs:

- ### SSH activity

- ### Failed logins

- ### System events

- ### Source IP trends
![image](https://github.com/user-attachments/assets/3e23c53b-7002-4118-a622-e128aa229fb1)
![image](https://github.com/user-attachments/assets/b8435d7f-7778-4d3d-a105-b84a5feb406f)
![image](https://github.com/user-attachments/assets/2bacbe9a-f340-47e7-a57b-758f0d209150)
![image](https://github.com/user-attachments/assets/821ed901-4b67-459b-b30c-268b867e648e)
![image](https://github.com/user-attachments/assets/0663ee17-06b0-4b2a-8b9f-f13efcfba4c3)
![image](https://github.com/user-attachments/assets/81f23e94-30f5-42ec-87ed-c53eb23346ed)

                    



