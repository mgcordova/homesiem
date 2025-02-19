<p align="center"><img src="https://images.contentstack.io/v3/assets/bltefdd0b53724fa2ce/blt0a8f8d63938463bc/5d01b52bae9baaf01450ac67/introducing-elastic-siem-2.png" alt="osTicket logo"/></p>

<h1>Create a Home SOC and Analyze Real-World Attack Data</h1>
This tutorial outlines how to set up a basic home SIEM with Elastic, configure elastic agents for collection, deploy a Kali Linux VM, generate and analyze security events using Nmap on Kali Linux.<br/>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Event Viewer
- Remote Desktop Connection
- Microsoft Sentinel
- Log Analytics Workspace

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- 

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

<p>Go to your Elasticsearch and search on the top right "Integrations</p>

![image](https://github.com/user-attachments/assets/feaa6707-9383-4c18-abca-17012baa0014)

<p>Install "Elastic Defend"</p>

![image](https://github.com/user-attachments/assets/cffef0c0-c032-46ec-82cd-0c29c456523d)

![image](https://github.com/user-attachments/assets/42048553-6f12-42b2-88d2-c57235e26846)

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



