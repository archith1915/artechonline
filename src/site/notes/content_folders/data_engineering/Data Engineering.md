---
{"dg-publish":true,"permalink":"/content-folders/data-engineering/data-engineering/","title":"Data Engineering","tags":["dataEngineering","data"],"dgShowToc":true}
---

Data engineering is the process of developing, implementing and maintaining systems that collect, process and serve large raw data.

# Data engineering lifecycle

1. Generation
2. Ingestion
3. Storage
4. Transforming
5. Serving

## Generation

The engineers source the data from various systems. They need to have a clear understanding as to how the data is generated, at what velocity, the format and schema, and the impact of fetching it.

They need to keep an open line of communication on the changes that can affect the pipeline and analytics.


The biggest challenge for data engineers would be the database structure and schema. Any change in the schema will require redefining of the pipeline and analytics code.

There are two categories of source systems - the traditional one, application databases and the most recent one, IoT swarms.

## Storage

Storage is an integral part of data engineering as it decides how well the data can be accessed and processed. Storage services offer different solutions. Some for structured data, some for unstructured (schemaless) while some for object storage. Some storage systems act merely as storage systems while some support advanced processing including querying and analytics.


## Data access frequency

Data access frequency decides the temperature of the data. Data that is fetched very frequently is called hot data, ex: user requests on a server. Hot data can be fetched several times a second.

Lukewarm data can be accessed say every week or month.

Cold data is often stored as backups for catastrophic events in archival facilities, nowadays cloud storages offered by several vendors for low costs.

## Ingestion

Ingestion plays a very important role in this lifecycle. It is the process of accessing or fetching the data from the source system. The source systems are usually outside the engineer's control and might stop working mysteriously. Or they may send poor and inconsistent data for storage and processing and thus needing regular maintenance and monitoring.


###  Batch v/s Stream Data


Most of the data we deal with is stream data. By stream we mean the data is available and transmitted in real-time. The latency for the data to be called real-time depends on the domain and requirements. Usually the data is accessed within seconds or even less than a second after it is generated.


Batch data is ingested either on a predetermined time interval or as the data reaches a preset size threshold. It is like accumulating data to a unit and then fetching it at once.


### Push v/s Pull

- **Push**: The source system **actively sends (pushes)** data to the target system as soon as the data is available or changes. The source "initiates" the data transfer.
    
- **Pull**: The target system **actively requests (pulls)** data from the source system on its own schedule. The target "initiates" the data retrieval.

## Transformation


The next stage of the data engineering lifecycle is transformation, meaning data needs to be changed from its original form into something useful for downstream use cases. Without proper transformations, data will sit inert, and not be in a useful form for reports, analysis, or ML.
