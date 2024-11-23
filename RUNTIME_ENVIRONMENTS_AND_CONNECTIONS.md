MODULE 2: RUNTIME ENVIRONMENTS AND CONNECTIONS

Module Objectives  
After completing this module, you will be able to:   
• Discuss Informatica Cloud runtime environments  
• Explore the Secure Agent architecture  
• View the Secure Agent log files  
• Define Connection  
• List types of Connectors  
• Discuss native and add-on connection types  

Informatica Cloud Runtime Environments  
What is a Runtime Environment?  
-A runtime environment is the execution platform that runs a data integration or application 
integration task. To run tasks in your organization, you must have at least one runtime environment 
set up in your organization.



Setting Up Runtime Environments:  
 Prerequesties.  
 License the Informatica Cloud Hosted Agent  
 -You can run tasks within the Informatica Cloud hosting facility if you license the Hosted Agent.
 The Informatica maintains the Hosted Agent runtime environment and agents.


In IICS, you can set up runtime environments in one of the following ways:

• Create one or more Secure Agent groups  
  -You can download and install one or more Secure Agents to run within your network or in a cloud
 computing services environment such as Amazon Web Services, Google Cloud, or Microsoft
 Azure.  
 -You can install only one Secure Agent on each physical or virtual machine.  
 -By default, a Secure Agent is added to its own group. You can add multiple agents to one Secure 
 Agent group if you have the Secure Agent Cluster license

Types of Runtime Environments  
Informatica Cloud supports the following runtime environments:
![image](https://github.com/user-attachments/assets/0b58dacd-7950-4423-9682-f8539acc8722)

1 Run synchronization, mapping, and replication tasks.  
2 Uses certain connectorssuch as Amazon S3, Google Analytics, Marketo, Microsoft Azure Blob Storage,
and Workday.  
3 Hosted Agent can process limited volumes of data.  
4 You cannot add, delete, or configure a Hosted Agent.  

Informatica Cloud Hosted Agent  
When you have the Cloud Runtime license in your organization, you can use the Informatica Cloud 
Hosted Agent to run the tasks.

Serverless Runtime Environment  
Serverless is a cloud architecture that allows you to build and run applications and services without 
managing servers, virtual machines (VMs), or containers. In serverless architecture, your 
application still runs on servers, but the server management is done by AWS. Using a serverless 
architecture allows developers to focus on their core product instead of managing and operating 
servers or runtimes.

To learn more about the Serverless Runtime Environment, click on the LEARN MORE button.
[LEARN MORE](https://informatica.csod.com/content/informatica/publications/5405/scormcontent/index.html#/lessons/RO_lj496Z11kWZ8PpHTFxiEf0vja4Bm9)

Informatica Cloud Secure Agent  
What is secure agent?  
-Secure agent is a light weight, self upgrading program that runs on our network. It enables secure
communication across the firewall both in and out vice versa.

![image](https://github.com/user-attachments/assets/c8da8818-3b52-46db-953c-6c6740e3a644)


Feature List  
Below is the list of features for IICS Secure Agent:  
Run-time version of PowerCenter execution component  
Available for Windows and Linux platforms  
One agent per machine  
Automatically links to the IICS Org you install it from  

You can install multiple agents within your network in following conditions:  
1. When you want separate agent machines with different controls/permissions for different 
businesses/user groups  
2. For failover purposes  
3. For additional processing power to run multiple tasks concurrently

Secure Agent services  
• Secure Agent services are pluggable microservices used for data processing.  
• Each service runs independently of the other service.  
The following table lists the IICS services and their description:  

![image](https://github.com/user-attachments/assets/20a9f02f-874b-4de4-ac2f-56d4c97cc581)


                       Configuring and Running Secure Agent   
Configuring Secure Agent  
To successfully install a secure agent on a Windows machine, you must configure the following   
properties:  
CONFIGURE THE FIREWALL  
If your organization uses a protective firewall, you must include the Informatica Intelligent Cloud
Services domain name or IP address ranges in the list of approved domain names or IP addresses.  

You should also enable port 443 (HTTPS) that the Secure Agent uses to perform all necessary
tasks through the firewall.  

The whitelists of domains and IP addresses can vary according to your data center, called a POD
(Point of Deployment).  

To identify the POD of your IICS Org, open the Org URL, and observe
the first few characters of the URL string.  
EXAMPLE: If the URL starts with usw3.dm-us.informaticacloud.com, then your POD is
USW3


You can find the whitelists of Informatica Intelligent Cloud Services domains and IP addresses for
different PODs from the link at the top of the Runtime Environments page in Administrator
service.

![image](https://github.com/user-attachments/assets/eaca6c3b-0621-4d8d-8d02-dde496c482fd)

CONFIGURE THE PROXY SETTINGS  

If your organization uses an outgoing proxy server to connect to the internet, the Secure Agent
connects to IICS through the proxy server.  

The Secure Agent installer configures the proxy server settings for the Secure Agent based on
settings configured in the browser. You can change the proxy server settings through the Secure
Agent Manager Proxy tab.
![image](https://github.com/user-attachments/assets/4b047be1-d42f-4f9b-9eee-cfe6fb2b9d80)

Running Secure Agent as Local/Network User   

If you are a user who runs the agent on a Window’s system, the agent inherits the access privileges 
of the Window’s user. This happens automatically when you install the agent. The agent needs 
permission to access the directories on Windows. Therefore, you may have to reconfigure the 
Windows service.

![image](https://github.com/user-attachments/assets/afb0c44c-b127-4857-b904-9348ce090659)




IICS Log Files  

When the Secure Agent runs a task, it generates the following log files:  

Session log  
The Secure agent generates session logs for all tasks that run in the Org. It provides technical
details about the task.  
Session logs are available at the following location:  
C:\Program Files\Informatica Cloud Secure Agent\apps\Data_Integration_Server\logs


Error log  
The error logs contain a list of all the bad records that the task failed to process. It also provides
the reason for task failure.  
The error logs are available in the following location:  
C:\Program Files\Informatica Cloud Secure
Agent\apps\Data_Integration_Server\data\error  


Success log  
The success logs contain a list of all records that the task processed successfully. The Secure
Agent does not generate success logs by default. You can enable the option in the
synchronization task wizard for the Salesforce target. It contains a record of all the rows that you
create, update, or delete.  

The success logs are available in the following location:  
C:\Program Files\Informatica Cloud Secure
Agent\apps\Data_Integration_Server\data\success

![image](https://github.com/user-attachments/assets/b55b9580-027a-4c07-bd11-a8e0e91cb8a4)


Infaagent log  
The infaagent log provides all the details of the network connectivity, the timing of the
successful connection, and attempts made to reconnect.  

The infaagent log is available in the following location:  
C:\Program Files\Informatica Cloud Secure Agent\apps\agentcore\infaagent.log


Tomcat log  
The tomcat log provides details about the task such as task start time, the request sent to the
Integration Server, and the response received from the Integration Server.  

The Tomcat log is available in the following location:  
C:\Program Files\Informatica Cloud Secure
Agent\apps\Data_Integration_Server\logs\tomcat

                                     Connections
What is a Connection?  
A connection is an Informatica Cloud object that provides access to data in the cloud and onpremise applications, platforms, databases, and flat files. It specify the location of sources, 
lookup objects, and targets included in a task. You can create a connection using connectors.  

Types of Connectors  
IICS provides two types of connectors:  

![image](https://github.com/user-attachments/assets/fefec593-48aa-4e12-8b09-deca9c49191b)

Some of the examples of Native and Add-on connectors are:

![image](https://github.com/user-attachments/assets/e474f320-b5c5-439b-86a6-6b4fb81f6230)


Using Add-On Connectors  

Before you can use an Add-on connector to create a connection, you need to add the connector to 
your IICS org. You can install a free trial version of the add-on connector, or you can buy the 
connector from Informatica.  

To add the connector, perform the following steps:  

1. Navigate to Administrator service.  
2. From the Add-On Connectors tab, select the connector.  
3. Click Free Trial to start using the connector.

   ![image](https://github.com/user-attachments/assets/79271a59-f20f-47f7-a1e5-3510be59c7c8)

After you install an add-on connector, it becomes available as a connection type for the 
organization and all sub-organizations.  

Note:- If you want to install an add-on connector to use it in a sub-organization, install the
connector in the parent organization. You cannot install an add-on connector in a suborganization.  


Creating a Connection  

In IICS, you can create connections in the following ways:  

From the Connections tab of the Administrator Service

               ![image](https://github.com/user-attachments/assets/58a21896-51bf-41cf-ab2d-879c499400ba)

From On-the-fly wizard while configuring a task

![image](https://github.com/user-attachments/assets/de1d68b1-a15f-4652-aebe-4f0aaf1c1053)

While creating a connection, you must specify the runtime environment for the connection. Except 
for Software-as-a-Service (SaaS) applications, all the connectors depend on the runtime 
environment for establishing connectivity with the data source. Therefore, you must install the 
Secure Agent in your IICS Org before creating any connection.  
After the connection is configured, it is available to all the users in the Org  











