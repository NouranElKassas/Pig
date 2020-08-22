# Download and Install Pig

Open terminal

Download Pig
```wget https://downloads.apache.org/pig/pig-0.17.0/pig-0.17.0.tar.gz```

extract Pig
```tar -xvf pig-0.17.0.tar.gz```

```su - hadoopusr```

Move the file from the current location to /usr/local/
```sudo mv pig-0.17.0 /usr/local/```

Open a File .bashsrc
```sudo gedit ~/.bashrc```

Add those Paths in the file

```
#Pig location 
export PIG_INSTALL=/usr/local/pig-0.17.0 
export PATH=$PATH:/usr/local/pig-0.17.0/bin 
```

Save and exit

to check the paths is already saved
```source ~/.bashrc```

To check if the Pig is working as MapReduce Mode
```pig```

To check if the Pig is working as Local Mode
```pig -x local```

Check Pig Version
```pig -version```
