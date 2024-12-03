### Amazon Storage Services

#### 12/03/2024 Session

* S3
    * Large scale of s3, Peta bytes
    * Hard Drives performance gets worse every year
    * Uses Disaggrageted storage
    * Build a smooth workload 
    * Data can be spread of millions of hard disks

* Data is hotter when it is young and cools down as it ages

* S3 is like limitless storage
* Except for limits that we have
* Amazon FSx like-for-like NAS relative to on-premise
* A new storage class for amazon by taking advantage of S3

* Amazon EFS achieved 10x inceease by focusing on performance
* Lifted throughput 2x via Luster and integrating with EFA

* Higher Bucket Limites resulted in a human to make that decision
* Raised bucket limits to 1,000,000 buckets

* S3 consistency
    * Made Puts viewable immediately
* S3 API Conditionals
    * Specify preconditions during an S3 request

* S3 express one zone
    * faster gets and puts requests
    * directory buckets for scaling S3 retrieval and lower costs
    * Less time and money on compute as well

* Data Lakes
    * use Parquet files
    * Format to represent a static table
    * Open table formets via Apache Iceberg
        * Supports input and output ops
  * AWS S3 Tables
    * first class managed table extractions inside S3
    * Delivers up to 3x faster query performance and 10x faster TPS 
    * Simplified table security with table-level perms
    * Continuously optimized
    * Fully integrated with other AWS services



