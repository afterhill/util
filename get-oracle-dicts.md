##Get all the tables of specified owner:

select * from sys.all_objects where owner='PRA_GLOBAL' and object_type='TABLE' order by object_name;

##Get all the fields of specified table:
```  
SELECT column_name as COLUMN_NAME, nullable || '       ' as BE_NULL,
  SUBSTR(data_type || '(' || data_length || ')', 0, 10) as TYPE
 FROM all_tab_columns WHERE table_name = 'ACCOUNT' order by COLUMN_NAME;
```
