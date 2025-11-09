# 🚀 Elastic Stack SIEM Home Lab 

<h2>Reference</h2>

 ### [By Abdullahi Ali](https://medium.com/@aali23/a-simple-elastic-siem-lab-6765159ee2b2)

<h2>Description</h2>

In this project, I set up a home lab for Elastic Stack Security Information and Event Management (SIEM) using the Elastic Web portal and a Kali Linux VM by following the instruction guide from the blog post listed. This hands-on experience allowed me to generate and simulate security events on the Kali VM, set up an agent to forward logs and event data to the Elastic SIEM, and query and analyze the ingested logs for actionable insights. This project helped to improve my understanding of SIEM workflows and log management using the Elastic Stack.
<br />

<h2>Environments Used </h2>

- <b>VMware Workstation on Windows laptop</b>
- <b>[Elastic Cloud account](https://cloud.elastic.co/registration)</b>

![SIEM LAB](https://github.com/user-attachments/assets/cb3500ed-e9b2-4c89-b038-245feb25f989)


<h2>Tasks Overview</h2>

- Install VMware  Workstation and create Kali Linux VM
- Set up Elastic account
- Configure the Elastic Agent on the Linux VM to collect the logs and forward it to the SIEM.
- Generate security events on the Kali VM.
- Query to find the security events in the Elastic SIEM.
- Create a Dashboard to visualize security events.
- Create alerts for security events.

- <h2>Task 1: Install VMware  Workstation and create Kali Linux VM </h2>
1. Download and install VMware Workstation from https://access.broadcom.com/default/ui/v1/signin/ on my Windows laptop. You need to create an account before downloading the software.
2. Download Kali Linux from https://www.kali.org/get-kali/#kali-virtual-machines.
3. Create a new VM with Kali Linux in VMware Workstation.
4. Start the Kali Linux VM and sign in with account kali, password is also kali.
   
![kali linux vm](https://github.com/user-attachments/assets/95f0c5d3-57c5-4d60-9e44-3bb76453aecf)

- <h2>Task 2: Set up Elastic account</h2>
1. Sign up for Elastic Cloud at https://cloud.elastic.co/registration. Choose the free 14-day trial option.
2. Log in to Elastic Cloud console at https://cloud.elastic.co.
3. Create my deployment by clicking on "Create Deployment". It went automatically to a default space. After creating it, I went back to manage my deployment and edit the solution view to Classic, then chose all features visibility: Analytics, Elasticsearch, Observability, Security, and Management.
   
<img width="1166" alt="Screenshot 2025-03-01 at 5 55 40 PM" src="https://github.com/user-attachments/assets/0f217728-a40b-4a17-a1c4-520c14ba06ed" />

4. Once the deployment is ready, click continue.

- <h2>Task 3: Configure the Elastic Agent on the Linux VM</h2>
1. To set up an agent to collect logs from your Kali VM and forward them to my Elastic SIEM instance, first I need to start from My Deployment, navigate to the Integrations page and click on Kibana main menu bar at the top left, then select “Add integrations” at the bottom.
   
<img width="238" alt="Screenshot 2025-03-01 at 6 10 05 PM" src="https://github.com/user-attachments/assets/8fe3114b-ed6b-4bf9-82fa-39f515a59fcf" />

2. Search for “Elastic Defend” and click on it and install it. Follow the instructions on the integration page and click on "Install Elastic Agent" to install the agent on Kali linux VM that I created.

<img width="1413" alt="Elastic Cloud" src="https://github.com/user-attachments/assets/bd842033-002c-4f03-93d9-aaddb0460e58" />


<img width="1131" alt="Kali Linux VM" src="https://github.com/user-attachments/assets/db54542d-fe6a-402f-b428-51bf8dc9a959" />

3. Copy the "Linux Tar" command and paste it into the Kali terminal.
   
![Install agent](https://github.com/user-attachments/assets/083dc8de-dafb-4a11-ac43-e6121b0ee5ba)

4. It takes a few minutes for the agent to be installed. Once that is done, the message "Agent enrollment confirmed" will show up. It will automatically start collecting and forwarding logs to the Elastic SIEM instance, and it might take a few minutes for the logs to appear in the SIEM.

![3](https://github.com/user-attachments/assets/ca58df53-25cf-4795-9338-0cdae2d2fed1)
![Elastic agent has been installed](https://github.com/user-attachments/assets/d9362fff-710f-46c2-bc96-6c9b4edb4a7e)


5. Verify that the agent has been installed correctly by running command: sudo systemctl status elastic-agent.service
   
![4](https://github.com/user-attachments/assets/090fc866-1fa5-4d1a-8df2-6305f79bbf11)

- <h2>Task 4: Generate security events on the Kali VM</h2>
1. Try to generate some security related events using Nmap tool. Open Kali terminal and run this command "sudo nmap <VM IP address>.
   
![5](https://github.com/user-attachments/assets/7662efdf-02a9-4b40-994e-e3f1be6fc835)

2. Try creating more events by running a few more Nmap scans, (“nmap -sS <ip address>”, “nmap -sT <ip address>”, “nmap -p- <ip address>”etc..”
![6](https://github.com/user-attachments/assets/bd71bc12-159e-410b-9c44-d3ad3daeb8b6)
![nmap command](https://github.com/user-attachments/assets/cfd225e8-ee2f-462b-b375-d63fbf96fdca)

- <h2>Task 5: Query to find the security events in the Elastic SIEM</h2>
1. Now I have generated events in Kali VM, it is time to view logs in Elastic agent. Click on the menu icon at the top-left with the three horizontal lines and then click on the “Logs” tab under “Observability” to view the logs from the Kali VM within the timeframe that I started creating the VM.
   
![obsevability logs](https://github.com/user-attachments/assets/dcd72089-fc6f-479a-b2b1-78688217d851)
   
![logs](https://github.com/user-attachments/assets/3a383f4f-9ded-4cd9-90a2-85ba77fef529)

2. Search for all logs related to Nmap scans, enter the query: event.action:“nmap_scan”. View and explore logs.

![nmap logs search](https://github.com/user-attachments/assets/68ad7d33-03a4-44bd-b305-3b7ba47a36ec)

- <h2>Task 6: Create a Dashboard to visualize security events</h2>
1. Create a simple dashboard that shows a count of security events over time by going to My Deployment on the web portal. Go to Analytics> Dashboard> Create dashboard> Create visualization.
2. Select "Area", then select “Count” as the vertical field type and “Timestamp” for the horizontal field in the metrics field. Then click "Save".

![7](https://github.com/user-attachments/assets/4253fa0d-e0ce-49e2-b5ea-84be1cd81c8c)

 - <h2>Task 7: Create alerts for security events</h2> 
 1. Create an alert in the Elastic SIEM instance to detect Nmap scans.Click on Security> Alerts> Manage rules> Create new rules. Under “Define rule”, select the “Custom query” option from the dropdown menu. Under “Custom query,” set the conditions for the rule. Use Nmap_scan, then click "Continue". Then set the rule's name and description under “About rule” section.
 2. Set the severity level for the alert, keep the default settings under “Schedule rule” and click “Continue”.
 3. Under "Actions", set the action I want to take when the rule is triggered by selecting email notification.
![Screenshot 2025-02-25 223157](https://github.com/user-attachments/assets/40e1d6b1-0f3d-48dd-a448-ac8094fd1eda)
![Screenshot 2025-02-25 223542](https://github.com/user-attachments/assets/5f43f7b6-4fa7-491c-a114-3d9a63aeb6ec)
![Screenshot 2025-02-25 224230](https://github.com/user-attachments/assets/e93e92a6-c72a-4d26-bd5d-6d1e69138fe0)
![11](https://github.com/user-attachments/assets/e5d3753a-3659-4972-93ad-4a17b774a608)

    
