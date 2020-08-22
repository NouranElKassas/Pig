#Analyize Pig Logs

Open terminal

Load Logs from logs.log
```log= LOAD '/logs.log';```

Iterate on the logs.log and save it in LEVELS 
```LEVELS= foreach log generate REGEX_EXTRACT($0,'(TRACE|DEBUG|INFO|WARN|ERROR|FATAL)',1) as LOGLEVEL;```

Neglect the logs that contains null
```FILTEREDLEVELS = FILTER LEVELS by LOGLEVEL is not null;```

Group the logs based on their type
```GROUPEDLEVELS= GROUP FILTERLEVELS by LOGLEVEL;```

The States are : TRACE, DEBUG, INFO, WARN, ERROR and FATAL

Get the number of times thie state appeared in the log file
```FREQUENCIES= foreach GROUPEDLEVELS generate group as LOGLEVEL, COUNT(FILTERLEVELS.LOGLEVEL) as count;``` 

Order the states by the frequent number of appearance descending
```RESULT = order FREQUENCIES by COUNT desc;```

Print the Result
```DUMP RESULT;```