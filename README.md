Hadoop Tool for CommonCrawl's WARC
=======================
This repository contains a Hadoop tool for dealing with the new CommonCrawl WARC data (http://commoncrawl.org/winter-2013-crawl-data-now-available/). It uses the UK Web Archive's (UKWA) WARC tools (https://github.com/ukwa/warc-discovery), which contains my earlier patches and which you will have to install first.

So
```bash
git clone https://github.com/ukwa/warc-discovery.git
cd warc-discovery
mvn install
cd ..
git clone https://github.com/hannesmuehleisen/commoncrawl-warc-hadoop
cd commoncrawl-warc-hadoop
# [add your payload to src/main/java/nl/cwi/da/commoncrawl/TagTool.java]
mvn assembly:assembly
```

To run this on Amazon EMR, you can simply add the produced JAR (warczenschwein-0.0.1-SNAPSHOT-job.jar) as a justom "Step", and add parameters, e.g. 

````
nl.cwi.da.commoncrawl.TagTool "s3://aws-publicdatasets/common-crawl/crawl-data/CC-MAIN-2013-48/segments/*/warc/"" s3://mybucket/output
````

