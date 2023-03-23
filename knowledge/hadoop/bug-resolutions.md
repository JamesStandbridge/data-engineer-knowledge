# Some bug resolutions

Exception in thread "main" org.apache.hadoop.hdfs.server.namenode.SafeModeException: Cannot delete /tmp/hadoop-yarn/staging/hadoop/.staging/job_1676028020656_0001. Name node is in safe mode.

### Solution

Disable safe mode

```bash
$ hdfs dfsadmin -safemode leave
```


No resource Manager running

### Solution

This can be a low storage alert

yarn.nodemanager.disk-health-checker.max-disk-utilization-per-disk-percentage = 90.0 % (default) and usage is beyond the 90%  per disk.

We can add this parameter into yarn-site.xml to increase the max limit

```xml
<property>
    <name>yarn.nodemanager.disk-health-checker.max-disk-utilization-per-disk-percentage</name>
    <value>100</value>
</property>
```


Could not find or load main class org.apache.hadoop.mapreduce.v2.app.MRAppMaster

### Solution