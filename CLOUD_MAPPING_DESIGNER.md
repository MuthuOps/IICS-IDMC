MODULE 4: CLOUD MAPPING DESIGNER    

Module Objectives    
After completing this module, you will be able to:  
• Discuss Cloud Mapping Designer  
• Define mappings  
• Explain field rules  
• Describe Mapping Tasks  
• Discuss Schema Handling  

Cloud Mapping Designer    

![image](https://github.com/user-attachments/assets/ec11c78d-e0dd-474d-91ad-21b7151dcd71)


Mapping Lifecycle    
A mapping lifecycle has the following stages:    

![image](https://github.com/user-attachments/assets/d3a49638-8314-44e5-86d5-9c8cd5695da0)

IICS Mappings    

A mapping is an asset that defines the flow of data from the source to the target.  
In IICS, you can create the following types of mappings:  

Data Integration Mapping or Mapping    
Used to deploy small to medium data integration solutions that are processed directly by a
Secure Agent group using the infrastructure that you provide, or by the Hosted Agent.  

Elastic Mapping  
Used to deploy large data integration solutions. When you run an elastic mapping, the  
mapping is pushed to an elastic cluster to achieve faster processing for broad data sets. The  
infrastructure of the elastic cluster is automatically optimized based on the number and size  
of elastic jobs.  

Mapping Features    
When you create a mapping, you can perform the following actions on the mapping:  

1. Copying Transformations  
You can use the Cloud Mapping Designer to copy transformations between mappings or   
mapplets. To copy one or more transformations, you must select the transformation(s) and click   
the Copy icon.

![image](https://github.com/user-attachments/assets/b4ea43e9-0d81-4b20-8123-d9671c27e47e)

2. Mapping Data Preview  
Mapping Data Preview allows users to preview the data for individual transformations to test the   
mapping logic. When you run the data preview, the Data Integration service displays the   
mapping results for the selected and the upstream transformations.  
You can preview data for a transformation on the Preview panel of that transformation. The   
preview results are stored in CSV files on the Secure Agent machine in the following location:  
<Secure Agent installationdirectory>/apps/Data_Integration_Server/data/cache/preview

![image](https://github.com/user-attachments/assets/0b52c68f-d5af-4587-90f2-576ab63c1201)

Points to Remember  
1. The data preview option is applicable for mapping with no validation errors in the  
selected or upstream transformation.  
2. Data preview is not supported for the following transformations:

Web Services transformation  
Sequence Generator transformation  
Target transformation  
Data Masking transformation  
Hierarchy Builder transformation  
Velocity transformation  

3. Customizing Preview Results    
When you run the data preview for a mapping transformation, you can select which columns to   
display or reorder the columns in the Preview panel of the mapping designer. You can customize   
the mapping preview from the Settings option in the Preview panel.

![image](https://github.com/user-attachments/assets/0030c332-d6dd-4992-997d-82f6a95946d4)

4. Data Flow Run Order    
When you create a mapping with multiple data flows, you can specify the data flow run order.
In a mapping, a ‘flow’ is all the connected sources, targets, and transformations in a mapping.
You can have multiple flows in a mapping.

You can specify the data flow run order when you want Data Integration to load the targets in the 
mapping in a particular order.  
EXAMPLE: You might want to specify the flow run order when inserting, deleting, or updating tables  
with primary or foreign key constraints. You can specify the flow run order for data flows with any  
target type.  

To configure the order in which the Data Integration runs the data flows in a mapping, perform   
the following steps in the Mapping Designer:  
START  
Step 1  
![image](https://github.com/user-attachments/assets/994712d5-825a-4048-b65d-5936515652d6)
Click Actions and select Flow Run Order.  

Step 2  
![image](https://github.com/user-attachments/assets/8457e741-10b9-4bc7-97d1-adfcb6e07f1f)

In the Flow Run Order dialog box, select a data flow, and use the arrows to move it up or down.
Once the run order is decided, click Save

Field Rules  
Field rules define how data enters a transformation from the upstream transformation. When there   
are no field rules defined in the mapping, then by default, all fields are included. You can define   
field rules for all the transformations, except the Source transformation. If you define multiple   
field rules, then the rules are evaluated in the specified order.  


Renaming Fields  
When renaming fields in IICS, consider the following points:  
Renaming fields avoids naming conflicts  
Rename fields individually or in bulk  
Field naming conflicts propagate throughout the data flow  
Rename fields before the transformation where the error occurred  
Can use a prefix, suffix, or pattern to rename fields in bulk  

Field Rules – Selection Criteria  
When you configure a field rule, you must specify the following field selection criteria to   
determine which incoming fields apply to the field rule.  

![image](https://github.com/user-attachments/assets/a7ead11f-210d-4097-b90f-03ec22064f90)

Mapping Task  
A mapping task allows you to process data based on the data flow logic defined in a mapping.  
When you create a Mapping Task, you must select a mapping to use in the task. Optionally, you   
can also define the following:  
1. Parameters that associate with the mapping  
2. Schedule to run the task  
3. Pre and post-processing commands for the task

Schema Change Handling  
Schema Change Handling defines how Data Integration handles changes made to data object
schemas.  
A schema change includes one or more of the following changes to the data object:  
1. Fields are added.  
2. Fields are deleted.  
3. Fields are renamed.  
4. Field data type, precision, or scale is updated.  
By default, Data Integration does not pick up the changes automatically. You can configure   
schema change handling on the Schedule page of a task.

Schema Change Handling Options  
When you enable dynamic schema change handling in a mapping task, you can configure how   
Data Integration applies schema changes from upstream transformations to each target.  
The following table describes the schema change handling options:  
![image](https://github.com/user-attachments/assets/7156e7d3-095a-4084-bb6b-646caa68242f)

1. You can see if a connector supports dynamic schema change handling using the help
section for that connector.  
2. You cannot enable dynamic schema change handling for hierarchical data.











