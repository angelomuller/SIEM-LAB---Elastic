# Overview :eyes:

This guide will walk you through setting up a home lab for Elastic Stack Security Information and Event Management (SIEM) using the Elastic web portal and a Kali Linux virtual machine. You’ll learn how to generate security events on the Kali VM, configure an agent to forward data to the SIEM, and query and analyze logs within the platform.

# Setting up :wrench:

In order to get this task done you'll need:

- Linux OS: I have recently started using Kali on VMWARE since my mentor mentioned VMWARE had less crashes and bugs over Vbox, but this task will normally  run on Virtualbox and;
- Account on Elastic: Head to https://elastic.co and create _your free trial account_.

With your account created and running, go to the main page and type _Defend_ on the search bar. Follow the prompts and install the integration on your kali.

<img width="2054" height="1434" alt="Screenshot_1" src="https://github.com/user-attachments/assets/b08a904d-cdba-45dd-9023-db0154ee205e" />
<img width="1750" height="1004" alt="Screenshot_2" src="https://github.com/user-attachments/assets/14fb345d-34ad-470c-aab2-8982d33ff7a9" />

Note: If you run into an error while trying to install elastic on Kali, probably will be related to the link avobe being expired. Try installing in root priviledge _(sudo -i)_ and use the following link instead - for x86 systems:

_cd ~ && curl -L -O https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-9.1.2-linux-x86_64.tar.gz && tar xzf elastic-agent-9.1.2-linux-x86_64.tar.gz && cd elastic-agent-9.1.2-linux-x86_64 && sudo ./elastic-agent install --url="https://1374d7b5ea2c44de84589f79d0613b30.fleet.us-central1.gcp.cloud.es.io:443" --enrollment-token="aFJtaG9KZ0JsQUpheXRpLTllTkE6N2N2VmNlVm9BRXhoNU1wOXc3VXpqQQ=="_

At the end you need to get a message like this on your command shell:

<img width="706" height="887" alt="Screenshot_3" src="https://github.com/user-attachments/assets/c6d49333-af43-476a-acb2-8b879ad909e6" />

To make sure the installation has been complete 100%, run the following command: _sudo systemctl status elastic-agent.service_

<img width="678" height="481" alt="Screenshot_5" src="https://github.com/user-attachments/assets/2aee9784-bf47-488b-832b-82cf90eefa05" />

Go back to your dashboard on Elastic and confirm the integration.

<img width="1830" height="1348" alt="Screenshot_4" src="https://github.com/user-attachments/assets/8fe8c806-186f-4d11-9ebc-4c4001e366c0" />

# Generating alerts on Kali :page_facing_up:

To confirm the agent is functioning, you can trigger security-related events on your Kali VM using a tool like Nmap. Nmap (Network Mapper) is a free, open-source utility for network exploration, management, and security auditing. It detects hosts and services on a network, mapping them out, scanning for open ports, identifying operating systems and software, and gathering other network details.

<img width="635" height="887" alt="Screenshot_6" src="https://github.com/user-attachments/assets/f2e9d0d2-cb25-4c78-8f36-16885b0bae77" />

Note: _localhost scan_ shows all services the host can talk to internally (good for privilege escalation checks) _versus your machine address scan_ simulates what an attacker sees over the network.

You can run some other scans such as masscan or rustscan for different inputs on our SIEM later.

<img width="679" height="353" alt="Screenshot_7" src="https://github.com/user-attachments/assets/a8b5e2a0-df53-48ad-9feb-749273f19f33" />

# Analyzing the events on Elastic Observability :microscope:

Now that we have created some events and forwarded to our SIEM (running on the background) we can check and start analyzing.
But in order to do that, first we need to set the Elastic feature called Observability. 

<img width="1987" height="985" alt="Screenshot_9" src="https://github.com/user-attachments/assets/dda9428f-fdfc-4e66-b536-da656424152b" />
<img width="1920" height="1260" alt="Screenshot_10" src="https://github.com/user-attachments/assets/94edb292-48ae-418d-9d34-a0ea3b87f3f4" />
<img width="2523" height="1261" alt="Screenshot_11" src="https://github.com/user-attachments/assets/dccd021a-476a-4655-a302-8adeb8a24ecc" />

Now inside Observability you need to open the Logs tab.

<img width="2486" height="1333" alt="Screenshot_12" src="https://github.com/user-attachments/assets/ac9100fd-986a-45a2-88fc-8d2b2fa01ada" />

In this page you have available what it's called _Telemetry_ which refers to the automatic collection, transmission, and analysis of data from systems, applications, or devices to monitor their performance, behaviour, and security.
You can also visualise alerts, create rules to filter specific commands you're chasing and so on.

<img width="2528" height="1263" alt="Screenshot_13" src="https://github.com/user-attachments/assets/e1cbe829-363d-49f2-8b15-c938f8cdc622" />
<img width="2523" height="1277" alt="Screenshot_15" src="https://github.com/user-attachments/assets/022ea895-0f6c-4d27-bda3-d67136add852" />
<img width="2257" height="1260" alt="Screenshot_16" src="https://github.com/user-attachments/assets/9ef24c74-a83b-4901-83ee-d67bf6807097" />
<img width="1933" height="1076" alt="Screenshot_17" src="https://github.com/user-attachments/assets/239b995b-4981-44eb-b25c-e245447ff188" />











