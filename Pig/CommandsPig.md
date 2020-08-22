# Pig Commands

open terminal

Add Files in Hadoop
```hadoop fs -put input /pigInput```

Print the data in the HDFS
```hadoop dfs -cat /pigInput```

Execute Pig in map reduce mode
```pig```

Load the data from HDFS to Pig
```
employee = LOAD '/pigInput' using PigStorage(',') AS ( ssn:chararray,name:chararray,department:chararray,city:chararray);
```

Print Result of employee
```DUMP employee;```

Print Employee's name and department

```
emp_foreach= foreach employee generate name, department;
```
Print Result of emp_foreach
```DUMP emp_foreach;```

Check how many employees is working in New York
```emp_filter = filter employee by city == 'New York';```

Print Result of emp_filter
```DUMP emp_filter;```

Order employees by ssn
```emp_order = order employee by ssn desc;```

Print Result of emp_filter
```DUMP emp_order;```

Store the data in the result in HDFS
```STORE emp_filter into '/pig_result';```





