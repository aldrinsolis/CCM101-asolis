# Mission Reflection

## 1. Why is object storage better suited for storing millions of photos compared to a traditional block storage hard drive?

Object storage is well suited for storing millions of photos because it is designed to manage large amounts of unstructured data. Each photo is stored as an object with its own unique identifier and metadata. Object storage can also scale as the amount of data increases, making it practical for applications that continuously receive user-uploaded images.

## 2. How did using Docker make it easier to deploy the MinIO storage server?

Docker made the deployment easier because I did not need to manually install and configure all the software required by MinIO. I only needed to run one Docker command with the required image, ports, container name, and environment variables. Docker also provided an isolated environment where MinIO could run consistently.

## 3. What is a "bucket" in the context of cloud storage?

A bucket is a logical container used to organize and store objects in an object storage system. In this activity, I created a bucket named `client-photos` where the uploaded sample file was stored. Buckets help organize data and make it easier to manage stored objects.

## 4. How do you think large enterprise companies ensure their object storage data is not lost if the physical server crashes?

Large enterprise companies can protect object storage data by keeping multiple copies or replicas of data across different storage devices or physical servers. They can also use backups, redundancy, data replication, and geographically separate storage locations. These methods help ensure that data remains available even when hardware fails.

## 5. How is your confidence in navigating the Linux command line growing?

My confidence in using the Linux command line is growing because I have practiced running Docker commands, checking containers, configuring ports, and deploying services. I also learned that small command errors can affect deployment, so I am becoming more careful when entering commands. This laboratory helped me understand how Linux commands are used in real cloud infrastructure tasks.
