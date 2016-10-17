CC = g++
CPPFLAGS = -I$(HADOOP_INSTALL)/include

max_temperature: max_temperature.cpp 
	$(CC) $(CPPFLAGS) $< -Wall -L$(HADOOP_INSTALL)/lib/native -lhadooppipes \
	-lhadooputils -lpthread -g -O2 -o $@ -lssl -lcrypto
