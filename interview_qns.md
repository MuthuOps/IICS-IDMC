![image](https://github.com/user-attachments/assets/0e72d154-cad6-4886-9887-958671b9a983)1, what is transformation in informatica?

* Transformations in informatica are informatica objects which is used to perform specific task that create    
  modify or pass data to defined target.  
* it used to modify the source data based on the target system requirements.  
* These transformations are classified into conected and unconnected.  
  when the transformation is connected to another transformation, it is connected.  
  and if it is standalone transformation, it is unconnected.  
* There are two types of transformations in informatics, that are active(row change) and passive(no row change)

2, What is Transaction Control Transformation?    
Transacion Control Transformation is an active transformation used to define commit ot rollback points dynamically.    

3, what is the difference between HOMOGENEOUS and HETROGENEOUS sources?    
* If a mapping is using only oracle sources ( table from same schema) or db2 or xml    
  or any other than they are called homogeneous sources.    

* HETEROGENEOUS if a mapping is using oracle source table, flat file, DB2 source and    
  xml source then they are called as heterogeneous sources    

4, what is sorted input in aggregator transformation in informatica?    
-> To increase session performance, sort the data for the Aggregator transformation.    
Use the sorted input option to sort data. The Sorted Input option decreases the use of   
aggregate caches. When you use the sorted Input option, the Data Integration Service assumes   
all data is sorted by group.  

5, Without sending sorted data to aggregator transformation..    
what will happen if sorted input setting is selected in the aggregator transformation?    
-> Sorted oinput for aggregator transformation will improve performance of mapping    
However, without sending sorted data to aggregator transformation and if sorted input    
setting is selected in the aggregator then the mapping result in the session failure.    


6, What will happen if you send the sorted data to aggregator but you are not selected sorted input    
option in the aggregator transformation?    
* Performance Impact:
  Without the "sorted input" option enabled, the Aggregator transformation will process
  data row by row, just like with unsorted data. This can result in slower performance,
  especially if you are dealing with a large dataset.
* Resource usage:
  The transformation may use more memory and processing resources to perform
  the aggregation, as it won't be able to take advantage of optimized algorithms
  for sorted data.

7, what will happen if i dont select any group by port in aggregator transformation?    
-> While using aggregator transformation, you need to check group by as the result returns    
each row by performing aggregation one by one and the passes to the pipeline.    
If no group by is checked, the last row will be processes and it will return only    
single row (last row) as it has no command to aggregate data.    

8, what will happen if you select all grouo by port in aggregator transformation?    
-> it will remove all the duplicated in the data.    

9, Diff between drop and delete and truncate
![image](https://github.com/user-attachments/assets/d483a4d1-f855-4794-a7da-beb4df8e669a)

10, 
![image](https://github.com/user-attachments/assets/ddb62345-0dc8-47f4-bd66-0bb4613c0594)


![image](https://github.com/user-attachments/assets/f545a46e-0633-47aa-acdb-a4b04a4035f4)


![image](https://github.com/user-attachments/assets/6e7eeb1a-5860-483f-89bc-25b4cc09351b)

![image](https://github.com/user-attachments/assets/db4f76c0-beca-4522-bb6c-ac9015ad9ce2)

![image](https://github.com/user-attachments/assets/963db904-2633-470c-9516-7a9d1ee01b5b)

![image](https://github.com/user-attachments/assets/5a912827-243e-4aa4-b11f-929844461e31)

pdo partitioning 
index...

cardinality

btree - high cardinality

bitmap index - low cardinality slower

reverse index - 

unique index- automatic for primary key

what ever fields after where or on join conditions

view index partition explain plan

![image](https://github.com/user-attachments/assets/0e9f07f5-45ff-43a6-af63-a92e7fcfcf1c)


I have extensive experience in development and administration activities, particularly in the automobile industry with Mercedes-Benz. In my development role, I have worked on integrating multiple data sources, including Oracle and Salesforce, by gathering requirements from customers, designing ETL mappings, creating test cases, performing unit testing, and facilitating SIT and UAT phases before deploying solutions to production after successful dry runs. I have also developed Unix scripts for monitoring secure agents and managing large cache creation mappings. On the administrative side, I have been instrumental in building new environments from scratch and successfully migrating organizations from one pod to another in Informatica while ensuring data integrity and minimal disruption. Additionally, I contributed to implementing SCIM integration for efficient user management. My role encompasses end-to-end ownership of processes, from requirement analysis to deployment and maintenance, ensuring seamless operations and high-quality deliverables.

An App Connection defines a link to a data source, a database, or a Service Connector



