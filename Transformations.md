MODULE 5: CLOUD MAPPING TRANSFORMATIONS  

Module Objectives  
After completing this module, you will be able to:  
• Define Transformation  
• Explain various types of transformations  
• Describe Mapplets  
• Use a Mapplet in Mapplet transformation  
• Use Query in a Mapping  

IICS Transformations  

What is a Transformation?  
A transformation is a mapping object that modifies the data in the mapping or passes it on to the   
next step of the mapping. In IICS, a transformation can be of two types:  
![image](https://github.com/user-attachments/assets/042c6d47-2e6e-41df-81cc-021874210856)

The transformations you can use in a mapping vary based on your organization's licenses. After   
adding a transformation to a mapping, you can define its details. Each transformation type has a   
unique set of options that you can configure.  
The following table provides a brief description of various IICS transformations. As we proceed   
furthur, we will discuss the other IICS transformations in detail  

![image](https://github.com/user-attachments/assets/339b9e30-a347-4dad-8fce-6a4f0683b7a1)
Note: The list of supported transformations can vary based on the IICS version.

Filter Transformation    
The Filter transformation filters data from the data flow depending upon the specified filter   
condition(s). A filter condition is an expression that returns either a TRUE or a FALSE value.  
When the filter condition returns a TRUE value for a row, the transformation passes the row to   
the rest of the data flow. If the filter condition returns a FALSE value, the row is dropped from   
the flow.  
In IICS, you can apply two types of filters in a mapping:  

* Simple Filter  
A simple filter condition includes a field name, a comparison operator, and a value.  
When you define multiple simple filter conditions in a mapping, the task evaluates the conditions  
in the specified order and evaluates the filter conditions using the AND logical operator.  
The task returns the rows that match all the filter conditions.  

* Advanced Filter  
Use an advanced filter condition to define complex expressions.  
When you configure a complex expression, you can incorporate multiple conditions using the  
AND or the OR logical operators.  
To improve job performance, you must place the Filter transformation close to the mapping  
sources to remove unnecessary data from the data flow.  

Expression Transformation    
An Expression transformation is a passive transformation that allows you to create new fields 
within the mapping.  
When you create a new field, you must specify the field name, type, precision, and scale. There   
are two types of fields in IICS:  
* Expression field:  
Defines the calculations that you perform on an incoming field and acts as the output field for  
results. You can use the field in the data flow.  

* Variable field:  
Holds a variable in the expression. You can use this field to store data temporarily, compare  
values, or to simplify complex expressions. A variable field is not available for use in  
downstream data flow.  


Union Vs Join  
Comparison  
The following table identifies some of the key differences between the Union transformation and   
the Joiner transformation.  

![image](https://github.com/user-attachments/assets/cfa8e2be-9852-406e-83c8-4b2fde7150bc)


Performing Lookup, Aggregation, and Normalization  

Lookup Transformation  
The Lookup transformation allows you to perform a lookup on relational tables, flat files, and   
views. To use a lookup transformation, you need to define the lookup object, lookup connection,   
lookup condition, and the return values. You must also specify how the lookup will behave if   
multiple matches are found during lookup.   

EXAMPLE: You can choose to return any row that matches, return the first row, return the last row,  
or report an error, and so on.  

You can use the following two types of Lookups in IICS:  
![image](https://github.com/user-attachments/assets/5f1387ad-bc29-4208-8fbf-0c82da78cc03)

Note:- You can use an unconnected lookup only with a database or flat-file data sources.  

Aggregator Transformation  
The Aggregator transformation is an active transformation that allows you to perform aggregate   
calculations, such as averages and sums on a group of data. To define how to group data for   
aggregate expressions, you can use the Group By fields in the Group By tab of the Aggregate   
transformation’s Properties panel.  

![image](https://github.com/user-attachments/assets/84e7a47e-653a-4d48-9c8e-35a39dfc8416)



