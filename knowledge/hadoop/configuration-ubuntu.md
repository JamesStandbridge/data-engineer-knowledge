# Hadoop

# Configuration Ubuntu 20.04

Edit file **************************************************etc/hadoop/core-site.xml************************************************** to configure hadoop in mode one node

```xml
<configuration>
    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://localhost:9000</value>
    </property>
</configuration>
```

Here we specify the name of the file system. All HDFS directories and files will be prefixed with hdfs://localhost:9000.

The **etc/hadoop/hdfs-site.xml** file contains the parameters specific to the HDFS file system. We edit it as follows:

```xml
<configuration>
    <property>
        <name>dfs.replication</name>
        <value>1</value>
    </property>
</configuration>
```

We specify here the number of replications of a block (which is 1 here).

Then you need to configure the MapReduce specific settings which are in the **etc/hadoop/mapred-site.xml** file:

```xml
<configuration>
    <property>
        <name>mapreduce.framework.name</name>
        <value>yarn</value>
    </property>
</configuration>
```

Here we specify that we will use YARN as our MapReduce implementation.

Finally we can also set up YARN via the **etc/hadoop/yarn-site.xml** file

```xml
<configuration>
    <property>
        <name>yarn.nodemanager.aux-services</name>
        <value>mapreduce_shuffle</value>
    </property>
</configuration>
```

We indicate here that there will be a shuffle operation.

Hadoop is now properly installed and configured. All that remains is to format the local HDFS file system and start Hadoop :

```bash
$ hdfs namenode -format
$ start-dfs.sh
$ start-yarn.sh
```

If you get the error: **pdsh@uer: localhost: rcmd: socket: Permission denied**, then the default rcmd of pdsh is rsh, not ssh, the remote login authentication of rsh and ssh is not the same, when installing hadoop we configured ssh localhost login without password, but rsh is not possible.

Simply add this new line in **~/.bashrc** (with user hadoop)

```bash
export PDSH_RCMD_TYPE=ssh

#then source the file
$ source ~/.bashrc
```