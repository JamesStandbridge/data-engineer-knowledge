# Hadoop

# Word Count test project

As hadoop user, compile the program as following :

```bash
$ export HADOOP_CLASSPATH=$($HADOOP_HOME/bin/hadoop classpath)
$ javac -classpath $HADOOP_CLASSPATH WordCount*.java
```

After this compilation (without error), you have to compress this program into a .jar:

```bash
$ mkdir -p hadoop/training/wordcount
$ mv *.class hadoop/training/wordcount
$ jar -cvf hadoop_training_wordcount.jar -C . hadoop
```

You can add text files in the input folder to test the program
For example with a random sample text

```bash
$ mkdir input
$ cd input
$ wget https://filesamples.com/samples/document/txt/sample3.txt
```

Then add the file in HDFS

```bash
# create a new input folder inside hdfs if not exist
$ hdfs dfs -mkdir /test-input
# then add the file
$ hdfs dfs -copyFromLocal ./sample3.txt /test-input/sample3.txt
```

And we can run our MapReduce program through the hadoop console client.

```bash
$ hadoop jar hadoop_training_wordcount.jar hadoop.training.wordcount.WordCountDriver /test-input/sample3.txt /results
```