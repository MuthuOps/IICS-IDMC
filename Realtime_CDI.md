MODULE Realtime scenario based questions in CDI  

Module Objectives  
After completing this module, you will be able to:  
• Able to know the basic to hard CDI workflows.  
• Able to use various CDI assets for DATA Flow.  



1, Header and footer in single target.  
--------------Rank(bottom)      
 source ->-------------------> UNION ->----------> target  
--------------Rank(top)  
Note: choose single row as return in rank.  
Also need to remember rank will sort the data according to its operation 
so in order to get output in right order sort the data after union or 
do rank in reverse order.


2.Store Previous row data in Next column. 
Sequence ->---- 
---------------> Expression ------> target 
Source ->------ 

Note: the expression will executed in the order of expression in it.  
expression rules for the requirement below:  
1, In_var = iif(NEXTVAL=1,NULL,in_previuos_salary)  
2, In_var = salarya (in_previous_salary)  
3, Out_var = step 1(result)  


3.Unique records and non unique records(duplicates) on different targets.  
---------> Aggregate----------> sorter->----  
-------------(group and count value)  
source---------------------------------------->Joiner ------> router(1 or >1)----->target  
--------->sorter(for another flow)->-----  
Note: before joining a flow from aggregator it should be sorted.  


4.SCD2 type data update.  
