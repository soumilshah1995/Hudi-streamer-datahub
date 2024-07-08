# Hudi-streamer-datahub
Hudi-streamer-datahub
![Screenshot 2024-07-08 at 5 20 36 PM](https://github.com/soumilshah1995/Hudi-streamer-datahub/assets/39345855/277d0a7c-0bdc-4836-a51c-62b350e59a98)


```
export JAVA_HOME=/opt/homebrew/opt/openjdk@11


#### Download dataset
* https://drive.google.com/drive/folders/1BwNEK649hErbsWcYLZhqCWnaXFX3mIsg?usp=share_link


# Download Jar Files
#### hudi-utilities-slim-bundle_2.12-0.14.0.jar
* https://mvnrepository.com/artifact/org.apache.hudi/hudi-utilities-slim-bundle_2.12

#### hudi-datahub-sync-bundle-0.14.0.jar
* https://mvnrepository.com/artifact/org.apache.hudi/hudi-datahub-sync-bundle




spark-submit \
  --class org.apache.hudi.utilities.streamer.HoodieStreamer \
  --packages 'org.apache.hudi:hudi-spark3.4-bundle_2.12:0.14.0' \
  --properties-file spark-config.properties \
  --master 'local[*]' \
  --executor-memory 1g \
  --jars /Users/soumilshah/IdeaProjects/SparkProject/apache-hudi-delta-streamer-labs/E1/jar/hudi-datahub-sync-bundle-0.14.0.jar \
   /Users/soumilshah/IdeaProjects/SparkProject/apache-hudi-delta-streamer-labs/E1/jar/hudi-utilities-slim-bundle_2.12-0.14.0.jar \
   --table-type COPY_ON_WRITE \
  --op UPSERT \
  --enable-sync \
  --sync-tool-classes org.apache.hudi.sync.datahub.DataHubSyncTool \
  --source-ordering-field replicadmstimestamp \
  --source-class org.apache.hudi.utilities.sources.ParquetDFSSource \
  --target-base-path file:///Users/soumilshah/IdeaProjects/SparkProject/apache-hudi-delta-streamer-labs/E1/silver/ \
  --target-table invoice \
  --props hudi_tbl.props
```
