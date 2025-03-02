# 🚀 Elastic Stack SIEM Home Lab 

<h2>Reference</h2>

 ### [By Abdullahi Ali](https://medium.com/@aali23/a-simple-elastic-siem-lab-6765159ee2b2)

<h2>Description</h2>

In this project, I set up a home lab for Elastic Stack Security Information and Event Management (SIEM) using the Elastic Web portal and a Kali Linux VM by following the instruction guide from the blog post listed. This hands-on experience allowed me to generate and simulate security events on the Kali VM, set up an agent to forward logs and event data to the Elastic SIEM, and query and analyze the ingested logs for actionable insights. This project helped to improve my understanding of SIEM workflows and log management using the Elastic Stack.
<br />

<h2>Environments Used </h2>

- <b>VMware Workstation on Windows laptop</b>
- <b>[Elastic Cloud account](https://cloud.elastic.co/registration)</b>

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
1. 


