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

4.Distinct records and duplicate on different targets.,

* type 1: (losing records)  
  ---------------------------------------------------------------------------------->target_1  
  source--------->aggregate (count) -----> router (count = 1 or not) -----  
  ---------------------------------------------------------------------------------->target_2

* type 2: ( without losing data)  
  ----------------------------------------------------->target_1  
  source------->Expression------>router(1 or >1)-------   
  ----------------------------------------------------->target_2
  Note: the expression will executed in the order of expression in it.  
  expression rules for the requirement below:  
  1, current data= input  
  2, store count = iff(step 1 = previous_record, count+1, 1)  
  3, previous_record = input  
  4, O_count = step 2


5.even and odd rows in different targets.  

* type 1:  
  ---------------------------------------------------------------------------------->target_1  
  Source-------> sequence -------> expression -----> Router(nextval=0 or not) ------  
  ---------------------------------------------------------------------------------->target_2  
  Note: the expression will executed in the order of expression in it.  
  expression rules for the requirement below:  
  1, O_nextval=MOD(nextval,2)  

* type 2:   
  ---------------------------------------------------------------------------------->target_1  
  Source-------> sequence -------> Router(MOD(nextval,2) = 0 or 1) ------  
  ---------------------------------------------------------------------------------->target_2

* type 3:  
  ---------------------------------------------------------------------------------->target_1  
  Source-------> sequence(cyclic 1 to 2) ------->Router(nextval=1 or 2) ------  
  ---------------------------------------------------------------------------------->target_2

6.header, footer and rest records in different targets.  

------------>sequence------->aggregateor(max,no group)----//////////////////////////////////////------>target(1 head)  
source------/////////////////////////////////////////----->joiner(full)----->router(1,or max,def)----->target(default)  
------------>sequence-------------------------------------///////////////////////////////////////----->target(max foot)  

Note:  
* when joining a data from aggregator should check the tick of sorted input.  
* when no group by selected in aggregator it will give last row as output.  
* use full outer join as aggregator will have 1 record and source will have full recors.  

7,covert column to row without using normalizer.  
------------>experssion(col1)------>sequence------   
source------>experssion(col2)------>sequence------>Union---->sorter---->target  
------------>expression(col3)------>sequence------  

Note:  
* sequence need to be there to get perfect alignment of conversion. 

8, convert row to column without using normalizer.  
* type 1 in single column  

  source------>expression----->aggregator---->target  

  Note:  
  1, for variable = IIF(id=prev_id,CONCAT(variable,dep ),dep)  
  2, then group by in aggregator

* type 2 in different columns

  source------>expression----->aggregator---->target

  Note:  
  1, for counter = IIF(id=prev_id,counter+1,1)  
  2, col1=if counter is 1 store here  
  3, col2=if counter is 2 store here  
  4, col3=if counter is 3 store here  

  2, then max each col in aggregator with group by id so all other null values in col will be omitted.

9, dynamic file creation using transaction control  

source------>sorter----->expression----->transactionControl----->target  

Note:  
* expression  
  ![image](https://github.com/user-attachments/assets/0dd5bc12-f867-469c-a21b-3ae8240655b3)  
* TC  
  ![image](https://github.com/user-attachments/assets/08dc35f2-a573-4476-9a1f-f7c1ad15dfa3)  
  iif(O_flag='YES',tc_commit_before,tc_continue_transaction)

* TGT  
  ![image](https://github.com/user-attachments/assets/e7261b80-6944-44c5-881f-58ccb36344a8)

* MC
  in post command we can execute this "rm output*.out" to avoid extra file generation.  

10, Load all the records except last 5 records. 

Source -----> sequence -----> sorter(to make decending on nextval)---->  
---------------------------------------------------------------------->filter(new nextval >5)---->target  
------------>sequence------------------------------------------------->  


Note:
cannot use active transformation upstream multiple times.  
new sequnce needed to filter because the old sequence already have some value done.  

11, load every 4th record into the target  

source------->sequence------>filter------>target   

Note:  
in sequence it should be cyclic and start from 1 and end with 4.  

![image](https://github.com/user-attachments/assets/1e77eb60-9eea-4ff8-8481-d92dff15a775)


