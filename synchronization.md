MODULE 3: SYNCHRONIZATION AND DATA TRANSFER TASK  

Module Objectives  
After completing this module, you will be able to:  
1. Define Synchronization Task  
2. Discuss Synchronization Task wizard  
3. Create a Synchronization Task  
4. Identify status of a Synchronization Task  
5. Discuss Data Transfer Task  
6. Discuss Activity Monitor and Activity Log  

Synchronization Task Overview  

A Synchronization Task allows you to synchronize the data between a source and a target.  
In IICS, the supported source and target types include Database connection, Flat File connection, 
and Salesforce connection.  

Some examples of business scenarios where you can use a synchronization task are:  
1. Read data from a flat file and write the data to Salesforce  
2. Apply Filter on incoming data before writing it to the target  
3. Transform data according to the business logic and update it on the target system
Synchronization Task Configuration

Definition Step  

The first step of the Synchronization task wizard is the Definition step. In this step, you need to 
specify the name, location, and description of the task. You also need to specify the operation 
that the task will perform.  

In IICS, a synchronization task can perform one of the following operations:  

INSERT OPERATION  

The Insert operation inserts all rows from the source into the target without taking the existing 
records into account. So, when you use the Insert operation, there is a risk of creating duplicate 
records in the target system. An ideal use case of this operation in a synchronization task is to 
perform a one-time load of data into the target system.  
Example:  
The source contains records A, D, E, and F. The target contains records A, B, C, and D. When 
you run a synchronization task with an Insert operation, duplicate records are created for A and 
D, as these two records already exist in the target  

![image](https://github.com/user-attachments/assets/099deb24-c568-4278-b809-381b0d163881)

![image](https://github.com/user-attachments/assets/ea49dfe6-b9ca-4abd-81b9-5386d3df2e0a)


UPDATE OPERATION  

When you run a task with the Update task operation, Data Integration updates rows in the target that exist in the source.  
If Data Integration finds a row in the source that does not exist in the target, the row fails.  

UPSERT OPERATION  

When you run a task with the Upsert task operation,  
Data Integration updates all rows in the target that also exist in the source and inserts all new source rows in to the target.  
If a source field contains a NULL value and the corresponding target field contains a value,  
Data Integration retains the existing value in the target field.  

DELETE OPERATION  

When you run a task with the Delete task operation,  
Data Integration deletes all rows from the target that exist in the source.  

Source Step  

The second step of the synchronization task wizard allows you to define the source information.  
The source for a synchronization task can be:  
1,Single Object  
When you specify the source type as single, you can perform an operation on a single source 
object. For example, a single Flat file.  
2,Multiple Object  
For multiple source types, you can configure multiple database tables or Salesforce objects as a
source for the synchronization task.  
3,Saved Query  
To use a Saved Query in a Synchronization Task, you must first create the Saved Query 
component. You can create a Saved Query from one or more database tables using a valid SQL 
SELECT statement  

Target Step  

The third step of the synchronization task wizard is to set up the target information. For a 
synchronization task, you can write data to:  
* Single Flat File  
* Database Table  
* Salesforce Object  
  
The target connections that you can use also depend on the task operation you select. For 
example, if you select the Upsert operation, you cannot use a flat-file target connection because 
you cannot Upsert records into a flat-file.  
After you select the target connection, you must select a target object. You can use an existing 
object, or you can create a new target at runtime.  
Note:- You can create a new target at runtime only for flat-file and relational database
connections.  

Data Filters  

Data Filter Step  
The fourth step of the synchronization task wizard is the Data Filters step. A data filter allows 
you to limit the data that you retrieve from the source. It acts like a WHERE clause of the query 
that retrieves records from the source.  
For a synchronization task, you can apply the following two types of data filters:  

* Simple Filter  
You can use a simple data filter when all the filter conditions can be joined together using
the AND operator. So, only those records that meet all the filter conditions will be passed to the
target.  
* Advanced Filter  
You can use an advanced data filter in the following conditions:  
• When the filter conditions are complex  
• When the connection is a flat-file connection  
• When it is necessary to use the OR operator in the data filter  
One of the main differences between a simple filter and an advanced filter is that, in an advanced 
filter, one expression contains all the filter conditions.

* Points to Remember  
• The filter type is determined based on the source connection type and the filter condition.  
• If your source type is a flat-file, then you must use the advanced data filter.  

* Data Filter Variables  
You can use the data filter variables to filter newly inserted records. For Upsert operation, you 
can use the system variables to filter records that have changed after a successful task run.  
IICS provides access to the following system variables:  
• $LastRunDate: Returns the last date on which the task ran successfully.  
• $LastRunTime: Returns the last time when the task ran successfully.  
• $ErrorFileName: Returns the name of the error file that gets generated.  
• $SuccessFileName: Returns the name of the success file that gets generated.  

![image](https://github.com/user-attachments/assets/78747a27-16ce-47d7-939a-c063d6964ced)

Field Mapping  

Field Mapping Step

The fifth step of the synchronization task wizard is the Field Mapping step. To complete the 
synchronization task configuration, you must define the mapping between the source fields and 
the target fields.  
IICS provides the Automatch feature to match source and target fields in a synchronization task.  
This feature matches the fields in the following two ways:  
1. Using Exact field Name  
2. By performing a Smart Match

![image](https://github.com/user-attachments/assets/1860bab9-fe86-4250-963c-95e4ff4939b8)

The Exact Field name option matches fields with the exact same name, and the Smart Match 
option matches fields with similar names.  
Example of Smart Match:  
You have a source field Cust_Name and a target field Customer_Name. The Smart Match 
function automatically links the Cust_Name field with the Customer_Name field.  
You can use the Clear Mapping option to clear the existing mapping or to rematch all the field 
mappings.  

Field Properties  

The following icons identify the field properties:  

1. Primary Key
   ![image](https://github.com/user-attachments/assets/d9201ac0-0a1e-4eb3-97c8-31e2cd8bc392)  
Indicates that the field is a primary key for the object  
2. External ID
   ![image](https://github.com/user-attachments/assets/1f38c819-55a2-4568-895a-41227fa519ce)  
Indicates that the field is an external ID for the object (Salesforce.com only)  
3. Non-null
   ![image](https://github.com/user-attachments/assets/b79bf02f-f652-4e36-a7b5-42e941a10ffd)  
Indicates that the field cannot contain a null value

Refresh Fields  

When you create a synchronization task, the Data Integration service stores field metadata for all 
the source and target fields. When you change the source or target of an existing task, you must 
use the Refresh Fields option to update the cache and view the latest field attributes.  

![image](https://github.com/user-attachments/assets/477f3878-9543-44b7-919a-fdcefa16489a)  

Edit Types and Validate Mapping  

In a Synchronization task, when you map the source fields with target fields, you must map the 
fields with compatible data types. To configure or edit the field data types, IICS provides 
the Edit Types option. This option is not available for all target types. If the synchronization task 
contains multiple sources or targets, first you need to select the source or target you want to edit, 
and then edit the data type.  
After you map the source and target fields, to check the validity of the task, use the Validate
Mapping option.  

Field Expressions  
What is Field Expression?  
Field expression allows you to transform the source data before you load it to the target.  
You can use field expressions in the following scenarios:  
• when you want to map multiple source fields to a single target field.  
• when you want to convert data values from one format to another format.  
• when you want to perform data clean-up activities, like trimming leading or trailing blank 
spaces, and, removing unnecessary characters.  

Example  

![image](https://github.com/user-attachments/assets/a01a873e-83e8-420e-ae69-8c245f8276dd)

When you drag and drop two source fields onto a single target field, IICS automatically writes 
the field expression.  
Example:  
When you drag phone and area code fields from the source and drop it onto the Phone Number 
field in the target, IICS automatically writes the field expression to concatenate Area Code and 
Phone Number. You can also edit this expression to perform additional formatting on the source 
fields, like adding space or adding parentheses around the area code.  

Field Lookup  
Using Field Lookup  
When synchronizing data between a source and a target, you can use the Field Lookup option to 
look for fields required for integration. This feature allows retrieval of information from any 
lookup connection based on the lookup condition defined for the task. This feature is useful 
when you have missing or inaccurate data.  
Note:- The lookup connection does not need to be the same as the source or the target
connection for the task.  

When you configure a field lookup, you must also configure how the Data Integration service 
handles multiple matching return values. The service can randomly choose a matching value or 
return an error. When the lookup returns an error, the Data Integration service writes the row to 
the error rows file.  

Example  
Consider an example where you can use Field Lookup to update the missing information.  

![image](https://github.com/user-attachments/assets/ce0b7a95-8e74-4253-9e45-e3fcf0ef8c83)

In the sample data, you can see that the state field contains no value. However, you have the zip 
code value available in the source.  
You also have a table that contains a list of zip codes and their associated states. So, you can use 
the table to perform a lookup on the Zip field.  
When the Synchronization task runs, it writes the lookup return value in the target. So, in this 
case, the value Texas is written to the State field in the target.  


Schedules  

Schedule Step  
The last step of the synchronization task wizard is the Schedule step.  
A schedule allows you to run tasks at a specific time or at regular intervals.  
For a synchronization task, you can create a schedule in the following two ways:  
1. From the Administrator service  
2. From the Schedule step of the task wizard
   
Additional Task Settings  
In the synchronization task schedule step, you can configure the following additional settings:

Email Notifications:  
Email notifications allow you to monitor   the status of the task. You can configure email 
notifications at the Org level or at individual task level.  
When you configure email notifications at the Org level, the notification applies to all tasks in 
the Org. When you configure email notifications at the individual task level, the notification 
applies only to that individual task.

SQL Commands:  
You can use SQL commands to perform database level tasks. The task runs pre-processing 
commands before it reads the data from the source. The task can also run post-processing 
commands after it writes the data to the target.  
You must note that if the pre or post-processing commands fail, the synchronization task 
also fails.  

Execution Mode:  
Execution mode defines the mode to run the task. There are two execution modes available for 
synchronization task – Standard and Verbose.  
In the standard execution mode, no debugging information is generated for the task. For the 
verbose execution mode, the mapping generates additional data in the logs that you can use for 
troubleshooting. It is recommended that you select the verbose execution mode only for 
troubleshooting purposes. The verbose execution mode impacts performance because of the 
amount of data it generates.  






