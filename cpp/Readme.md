# Run CPP file within hadoop
### You must first install the required packages.
We need to have compilers and make utility first. To install it use root account and execute
```apt-get install build-essential```

Now we need SSL library also. To install the library, execute
```apt-get install libssl-dev```

Thats all. Now you can compile and run your C++ MapReduce application.
Login to hadoop user and change to directory cpp/MaxTemperature, and use `make` command to compile it.

To execute our application we need to put sample files to hdfs. To do this just use
```hdfs dfs -put sample.txt```
To verify your copy operation use  `hdfs dfs -ls` command and see if sample.txt is there.

Now you need to put max_temperature executable file to hdfs, under bin directory.
```
hdfs dfs -mkdir bin
hdfs dfs -put max_temperature bin
```
Now we are ready to execute.
```
hadoop pipes \
  -D hadoop.pipes.java.recordreader=true \
  -D hadoop.pipes.java.recordwriter=true \
  -input sample.txt \
  -output output \
  -program bin/max_temperature
```

Thats all.

