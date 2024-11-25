Module : Data Transfer Task  

Module Objectives    
After completing this module, you will be able to:    
• Define  Data Transfer Task     
• Discuss  Data Transfer Task wizard    
• Create a  Data Transfer Task    

A data transfer ask allows you to transfer data from a supported IICS source to a supported 
target.  
When you configure a data transfer task, you specify one of the task operations based on your 
selected target:  
1. Insert  
2. Update  
3. Upsert  
4. Delete  
For a data transfer task, you can augment the source data with a lookup source. Depending upon 
the source connection, you can also sort and filter the data before loading it to the target. In the 
case of multiple filters or sort conditions, the task applies the conditions in the listed order.  
Note:- To create and run data transfer tasks, you need the Data Integration 
Advanced license.

Data Transfer Task Sources  
When configuring a data transfer task, you can use two data sources in a single task.  
First Data Source Acts as the source for the data transfer task.  
Second Data Source Acts as the lookup source for the data transfer task.  
The task queries the lookup source based on the specified lookup condition and returns the lookup 
result to the target. The use of a second source is optional. You can use a second source to augment 
the source data with a related value or values from the lookup source.  
To optimize performance, the task caches the lookup source. The cache remains static and does 
not change as the task runs. The cache files are removed after the task completes.  

Sample image of Second Source configuration    

![image](https://github.com/user-attachments/assets/0a43ca6a-a5fd-4f68-b8fb-e5152e3eb100)

Activity Monitor    

When you start a task, the Activity Monitor displays the status of the current and previously ran 
tasks. You can also view the job details and download a session log while a job is running so that 
you can easily monitor long running jobs. You can also stop a running task, restart a previous 
task, or refresh the status of a currently running task from the Activity Monitor.    

![Uploading image.png…]()

Task Status    

A synchronization task can have one of the following statuses:  

Starting : Job is starting  
Running  : Job is in progress  
-----------Success Job ran successfully without errors  
Failed   : An error caused the job to fail  
-----------No rows were moved from source to target  
Warning  : Job completed but some rows failed  
-----------Review the Error Rows file to identify failed rows and review error messages  
