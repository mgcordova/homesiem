<p align="center"><img src="https://images.contentstack.io/v3/assets/bltefdd0b53724fa2ce/blt0a8f8d63938463bc/5d01b52bae9baaf01450ac67/introducing-elastic-siem-2.png" alt="osTicket logo"/></p>

<h1>Create a Home SOC and Analyze Real-World Attack Data</h1>
This tutorial outlines how to set up a basic home SIEM with Elastic, configure elastic agents for collection, deploy a Kali Linux VM, generate and analyze security events using Nmap on Kali Linux.<br/>

<h2>Environments and Technologies Used</h2>

- Elastic SIEM
- Linux Kali VM

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Set up a free Elastic account
- Install the Kali VM
- Configure the Elastic Agent on the Linux VM to collect the logs and forward it to the SIEM.
- Generate security events on the Kali VM
- Query to find the security events in the Elastic SIEM.
- Create a Dashboard to visualize security events.
- Create alerts for security events.

<h2>Set up an Elastic Account</h2>

<p>Create an account with a free trial (https://cloud.elastic.co/registration) 

Start your trial, go to the console (https://cloud.elastic.co/home) and click "Create Deployment" and select "Elasticsearch" as the deployment type.

Choose a region and deployment size that fits your needs and click on “Create Deployment.”

Once, deployment is ready click "continue".</p>

![image](https://github.com/user-attachments/assets/5c7e3b27-bf55-4e4f-8024-afc6a8909fd7)

![image](https://github.com/user-attachments/assets/c4bbe33b-ea84-4ee7-afe4-a2cf2755f1e7)

<h2>Set up the Linux VM</h2>

<p>Download Python (https://www.python.org/downloads/)

After installing python, open CMD and type "-m pip install pywin32"

Follow the instructions if it asks you to update python 

![image](https://github.com/user-attachments/assets/c3a444fe-f4e9-4cb1-badf-2b22993e31f8)

![image](https://github.com/user-attachments/assets/0fb66df7-c010-401c-9e09-cfb60c6f2612)

Download and install VirtualBox (https://www.virtualbox.org/wiki/Downloads) 

![image](https://github.com/user-attachments/assets/cea07642-dfd3-4b25-9f09-f089d8c0aab9)

Download and install a Kali VM [Virtual Box] (https://www.kali.org/get-kali/#kali-platforms)

Extract the folder

Open VirtualBox and select the Kali VM folder by pressing "Add"</p>

![image](https://github.com/user-attachments/assets/0972746d-173e-43e2-8cdd-ec75ae0ed4ea)

![image](https://github.com/user-attachments/assets/2dcbfc61-1539-4d28-b875-2b1edcb420b7)

<p>Power on the VM by double clicking the newly added Kali VM

Once the installation is complete, log in to the Kali VM using the credentials “kali” for both the username and password.<</p>

![image](https://github.com/user-attachments/assets/fef8e0f3-da18-40d8-9b79-d32c8eb3ae2f)

<p>Check connectivity by pressing Terminal Emulator and typing "uname -a"</p>

![image](https://github.com/user-attachments/assets/de8a0e2b-f777-4ad5-ae8f-e874fbde9122)

<h2>Setting up the Agent to Collect Logs</h2>

<p>Go to your deployment and select Open Kibana and search on the top right "Integrations</p>

![image](https://github.com/user-attachments/assets/f59a75a8-72a3-47d2-a1ec-46826ea1c5fc)

<p>Install "Elastic Defend"</p>

![image](https://github.com/user-attachments/assets/cffef0c0-c032-46ec-82cd-0c29c456523d)

<p>Once installing you will be prompted to install Elastic Agent on your host. Copy the command paste it into your terminal</p>

![image](https://github.com/user-attachments/assets/259c9574-25be-42a0-8387-5da9d2c3d353)

![image](https://github.com/user-attachments/assets/99006267-0590-4b0e-93a1-3cdd88a1232a)

<p>Continue setting up Elastic Defend</p>

![image](https://github.com/user-attachments/assets/63c2f8f7-dc3f-4600-8d4b-27f8a24f5fde)

<h2>Generating Security Events on the Kali VM</h2>

<p>In your terminal type "nmap -p- localhost"

Then type "sudo nmap -sS localhost"</p>

![image](https://github.com/user-attachments/assets/dc03e700-e577-4639-976d-3ebe397d82a4)

![image](https://github.com/user-attachments/assets/211dc5a2-68fb-4eef-897a-75ba3853238b)

<h2>Querying for Security Events in the Elastic SIEM</h2>

<p>Open the menu on the top left, click Discover and type in the search bar "process.args nmap". The nmap commands we put in the terminal should be in these logs</p>

![image](https://github.com/user-attachments/assets/151278b5-808b-4d17-909f-61f8192a2765)

<h2>Create a Dashboard to Visualize the Events</h2>

<p>Go on the top right and search "Dashboards"</p>

![image](https://github.com/user-attachments/assets/0eba3c0e-7b12-4bef-b43b-d933a9626270)

<p>Click on the “Create dashboard” button on the top right to create a new dashboard.

Click on the “Create Visualization” button to add a new visualization to the dashboard.

Select “Bar” as the visualization type. This will create a chart that shows the count of events over time.

In the “Metrics” section of the visualization editor on the right, select “Count” as the vertical field type and “Timestamp” for the horizontal field. This will show the count of events over time.</p>

![image](https://github.com/user-attachments/assets/1be6fde3-177a-4a27-b38b-76da03c3e879)

<p>Add some more events by typing the following commands in the Linux Terminal

"sudo -l"

"sudo ps"

"mkdir foobar"

"nmap -sV localhost"

"nmap www.simplycyber.io</p>

![image](https://github.com/user-attachments/assets/138896ce-d951-4dbf-a5df-8b0b0b72380a)

<h2>Create an Alert</h2>

<p>On the top right search up "Rules", click create rule

Select "elasticsearch query"

Select KQL Query and define the query as

event.action: "nmap_scan"

For the action, click email and fill out the email to send the alerts to. The subject can be something like "NMap Scan Detected"</p>

![image](https://github.com/user-attachments/assets/76d1b9ab-877c-42bf-9a6c-fb5df261fbdd)

![image](https://github.com/user-attachments/assets/e1d0ca59-3f36-40ec-a536-70e852d50201)

<hr>

<p>In this tutorial, we have set up a home lab using Elastic SIEM and a Kali VM. We forwarded data from the Kali VM to the SIEM using the Elastic Beats agent, generated security events on the Kali VM using Nmap, and queried and analyzed the logs in the SIEM using the Elastic web interface. We also created a dashboard to visualize security events and then created an alert to detect security events.</p>
