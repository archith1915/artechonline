---
{"dg-publish":true,"permalink":"/content-folders/core-subjects/bda/matrix-multiplication/"}
---

# MatrixMultiplyMapper.java

```java
public class MatrixMultiplyMapper extends Mapper<LongWritable, Text, Text, Text> {

    public void map(LongWritable key, Text value, Context context) {

        String[] parts = value.toString().split(",");

        String matrix = parts[0];

        int i = Integer.parseInt(parts[1]);

        int j = Integer.parseInt(parts[2]);

        int val = Integer.parseInt(parts[3]);

        if (matrix.equals("A")) {

            for (int k = 0; k < P; k++) {

                context.write(new Text(i + "," + k), new Text("A," + j + "," + val));

            }

        } else if (matrix.equals("B")) {

            for (int k = 0; k < M; k++) {

                context.write(new Text(k + "," + j), new Text("B," + i + "," + val));

            }

        }

    }

}
```

> [!info] **P** is the number of **columns** in **B** and **M** is the number of **rows** in A

# MatrixMultiplyReducer.java

```java
public class MatrixMultiplyReducer extends Reducer<Text, Text, Text, IntWritable> {

    public void reduce(Text key, Iterable<Text> values, Context context) {

        Map<Integer, Integer> amap = new HashMap<>();

        Map<Integer, Integer> bmap = new HashMap<>();

        for (Text val : values) {

            String[] parts = val.toString().split(",");

            String tag = parts[0];

            int k = Integer.parseInt(parts[1]);

            int v = Integer.parseInt(parts[2]);

            if (tag.equals("A")) {

                amap.put(k, v);

            } else {

                bmap.put(k, v);

            }

        }

        int sum = 0;

        for (int k : amap.keySet()) {

            if (bmap.containsKey(k)) {

                sum += amap.get(k) * bmap.get(k);

            }

        }

        context.write(key, new IntWritable(sum));

    }

}
```

# MatrixMultiplyDriver.java

```java
public class MatrixMultiplyDriver {

    public static void main(String[] args) throws Exception {

        Configuration conf = new Configuration();

        Job job = Job.getInstance(conf, "Matrix Multiply");

        job.setJarByClass(MatrixMultiplyDriver.class);

        job.setMapperClass(MatrixMultiplyMapper.class);

        job.setReducerClass(MatrixMultiplyReducer.class);

        job.setOutputKeyClass(Text.class);

        job.setOutputValueClass(Text.class);

        FileInputFormat.addInputPath(job, new Path(args[0]));

        FileOutputFormat.setOutputPath(job, new Path(args[1]));

        System.exit(job.waitForCompletion(true) ? 0 : 1);

    }

}
```