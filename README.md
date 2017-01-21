# Scala_WordCount
Word count Program in Scala

You must have seen Hadoop word count program in java, python or in c/c++ but probably not in Scala. so, lets learn how to build Word Count Program in Scala.

Submitting a Job to Hadoop which is written in Scala is not that easy, because Hadoop runs on Java so, it does not understand the functional aspect of Scala.
For writing Word Count Program in Scala we need to follow the following steps

    Create Scala Project with Sbt having version of your choice.
    Add Hadoop core Dependency in build.sbt from https://mvnrepository.com/artifact/org.apache.hadoop/hadoop-core.
    Create Scala object say WordCount with main method in the project.
    Create a class under the Scala object say Map that extends MapReduceBase class with Mapper class.
    Provide body to Map Function.
    Create another class under Scala object say Reduce that extends MapReduceBase class with Reduce class.
    Provide body to reduce function.
    Provide necessary job configuration in main method of Scala object.

Here is the example for Word Count Program written in Scala.

Till now we have created a program in Scala, now we need to submit this Program/ Job to Hadoop. For submitting a job to Hadoop we need to follow certain steps.

    Add sbt-assembly plugin to plugin.sbt under project from https://github.com/sbt/sbt-assembly.
    Open terminal and change directory to the root of the project.
    In terminal run the command sbt clean compile assembly
    This command will build the jar under target/scala<version> folder of project.
    Create directory in HDFS by the following commnad.

    $HADOOP_HOME/bin/hadoop fs -mkdir input_dir 

    Insert some data in newly created directory in HDFS by following command.

    $HADOOP_HOME/bin/hadoop fs -put sample.txt input_dir 

    Now Submit job to Hadoop by following command.

    $HADOOP_HOME/bin/hadoop jar jar_name.jar input_dir output_dir 

the jar in the last command is same which is stored in target/scala<verion> directory of project.

you can see the output by the following command

`$HADOOP_HOME/bin/hadoop fs -ls output_dir/`

if you encounter any problem regarding the building of jar using sbt clean compile assembly command then you need to include mergeStrategy in build.sbt you can find related information [here](https://github.com/sbt/sbt-assembly).
