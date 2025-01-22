1, what is transformation in informatica?

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
