# Hadoop

# Installation Ubuntu 20.04

## Step 1 - Installing Java

```bash
$ sudo apt update
$ sudo apt install openjdk-11-jdk
```

## Step 2 - Create a Hadoop User

```bash
$ sudo adduser hadoop
```

## Step 3 - Configure SSH Key-based Authentification

```bash
$ su - hadoop
$ ssh-keygen -t rsa
$ cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys 
$ chmod 640 ~/.ssh/authorized_keys
$ ssh localhost  #test
```

## Step 4 - Installing Hadoop

```bash
$ su - hadoop

# current version feb 2023 is 3.3.4
$ wget https://dlcdn.apache.org/hadoop/common/current/hadoop-3.3.4.tar.gz
$ tar -xvzf hadoop-3.3.4.tar.gz
$ mv hadoop-3.3.4 hadoop
```

Open the **~/.bashrc** to configure hadoop and java environment variables on your system.

```bash
$ nano ~/.bashrc
```

Append the below lines to file. We can find JAVA_HOME location by running :

```bash
$ dirname $(dirname $(readlink -f $(which java)))
```

Don't forgot the source the bash file in order to apply changes :

```bash
$ source ~/.bashrc
```

The lines : 

```bash
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export HADOOP_HOME=/home/hadoop/hadoop
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export HADOOP_YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
```

Open the Hadoop environment variable file :

```bash
$ nano $HADOOP_HOME/etc/hadoop/hadoop-env.sh
```

And set the JAVA_HOME with same value as bashrc :

```bash
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
```

If all went well, this command should work :

```bash
./$HADOOP_HOME/bin/hadoop
```