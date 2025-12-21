---
{"dg-publish":true,"permalink":"/content-folders/core-subjects/bda/word-count/"}
---

# WordCounterMap.java

```java
public class WordCounterMap extends Mapper <LongWritable, Text, Text, IntWritable> {

    protected void map (LongWritable key, Text value, Context context) throws IOException, InterruptedException {

        String[] words = value.toString().split(",");

        for(String word : words){

            context.write(new Text(word), new IntWritable(1));

        }

    }

}
```


# WordCounterReduce.java

```java
public class WordCounterReduce extends Reducer <Text, IntWritable, Text, IntWritable> {

    protected void reduce(Text word, Iterable<IntWritable> values, Context context) throws IOException, InterruptedException {

        Integer count = 0;

        for(IntWritable val : values){

            count += val.get();

        }

        context.write(word, new IntWritable(count));

    }

}

```

# WordCounterDriver.java

```java
public class WordCounterDriver{

  public static void main(String args[]) throws IOException, InterruptedException, ClassNotFoundException {

    Job job = new Job();

    job.setJobName ("wordcounter");

    job.setJarByClass(WordCounter.class);

    job.setMapperClass(WordCounterMap.class);

    job.setReducerClass(WordCounterReducer.class);

    job.setOutputKeyClass(Text.class);

    job.setOutputValueClass(IntWritable.class);

  

    FileInputFormat.addInputPath(job, new Path ("/sample/path/word.txt"));

    FileOutputFormat.addOutputPath(job, new Path ("/sample/path"));

    System.exit(job.waitForCompletion(true)? 0 : 1);

  }  

}
```