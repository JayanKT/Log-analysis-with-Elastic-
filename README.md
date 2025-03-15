## 📌 Project: Implementation of Atomic Red Team for Windows Event Logs in an Elastic Stack Environment  

### 🎯 Objective  
The project aims to establish a security monitoring system utilizing the Elastic Stack to ingest, store, and analyze Windows Event Logs generated through Atomic Red Team (ART) attack simulations. This setup provides insights into adversarial techniques and enhances threat detection capabilities.  

### 🛠 Skills Learned  
✔ Practical experience with Security Information and Event Management (SIEM) concepts.  
✔ Proficiency in configuring and deploying Elastic Stack components.  
✔ Hands-on experience with Windows Event Logs analysis.  
✔ Implementation and execution of Atomic Red Team simulations.  
✔ Detection and visualization of attack scenarios using Kibana dashboards.  
✔ Development of theoretical detection rules for security monitoring.  

### 🔧 Tools Used  
- **Elastic Stack** (Elasticsearch, Kibana, Winlogbeat) – For log ingestion, storage, and visualization.  
- **Atomic Red Team (ART)** – For simulating real-world adversary tactics.  
- **Windows Event Logs** – For capturing and analyzing security-related logs.  
- **Oracle VirtualBox** – For virtualized testing environment.  
- **PowerShell** – For executing ART test scenarios.  

### 🔹 Steps  
#### ✅ Environment Setup  
- Created two Virtual Machines:  
  - **Windows 10 VM:** Running ART simulations and collecting event logs using Winlogbeat.  
  - **Ubuntu VM:** Hosting Elasticsearch and Kibana for log storage and visualization.  
- Configured a NAT network for seamless communication between VMs.
  
 ![image](https://github.com/user-attachments/assets/b80c04dc-42cd-48ff-8eb3-3e9136d1ca7b)

 
#### ✅ Deployment of Components  
##### 📌 Atomic Red Team (ART) Setup  
- Installed and configured ART on Windows 10 VM.  
- Executed multiple attack scenarios.  

##### 📌 Winlogbeat Configuration  
- Captured and forwarded Windows Event Logs to Elasticsearch.  
- Monitored security, system, and PowerShell logs.
 
![image](https://github.com/user-attachments/assets/565f0ce4-e848-4ade-a981-8814f8384166)

##### 📌 Elasticsearch & Kibana Setup  
- Configured Elasticsearch for data indexing.  
- Created Kibana dashboards for log visualization and analysis.  

![image](https://github.com/user-attachments/assets/e2155323-8223-4223-a057-e71058cad829)
![image](https://github.com/user-attachments/assets/ba8bd5f3-8337-4f6a-80be-39e5f2717fd2)

### ⚠ Simulated Attack Scenarios  
#### 🔍 Ref 1: Creating a New Local User (**T1136.001**)  
- **Attack Execution:** Used PowerShell to create unauthorized user accounts.  
- **Captured Logs:** Event ID **4720** (user account creation) and related changes.  
- **Visualization:** Monitored account creations and modifications in Kibana dashboards.  

![image](https://github.com/user-attachments/assets/ee7e02a0-4b7a-4395-bb87-369fb2a3c2b7)

#### 🔍 Ref 2: Brute Force Attack (**T1110.001**)  
- **Attack Execution:** Simulated multiple failed login attempts.  
- **Captured Logs:** Event ID **4625** (failed logins) and Event ID **4740** (account lockout). - **Visualization:** Displayed failed login attempts and account lockout events.  

![image](https://github.com/user-attachments/assets/48f2c1a5-3c3b-4225-91d3-23eefc4882b8)

#### 🔍 Ref 3: Clearing Windows Event Logs (**T1070.001**)  
- **Attack Execution:** Used PowerShell to clear security logs.  
- **Captured Logs:** Event ID **1102** (security log cleared) and Event ID **104** (PowerShell log cleared).  
- **Visualization:** Tracked log-clearing activities in Kibana dashboards.  

![image](https://github.com/user-attachments/assets/b95a5da7-1533-46ca-b34e-7054ae11f1cd)

### 🔎 Detection Rules (Sample Kibana Queries)  

#### 🚨 Detecting Unauthorized User Creation  
{ "query": { "match": { "winlog.event_id": "4720" } } }
 
#### 🚨 Detecting Brute Force Attacks
{ "query": { "range": { "winlog.event_id": { "gte": 4625, "lte": 4625 } } } }

#### 🚨 Detecting Log Clearing Activites
{ "query": { "match": { "winlog.event_id": "1102" } } } 


### 🔮 Future Improvements

- Expand ART scenarios for broader security assessment.

- Optimize Elasticsearch for improved query performance.

- Enhance Kibana dashboards with more detailed visualizations.

- Integrate automated response mechanisms for threat mitigation.

This project serves as a foundation for leveraging Elastic Stack and ART for real-world security monitoring, emphasizing the importance of proactive threat detection and incident response.
