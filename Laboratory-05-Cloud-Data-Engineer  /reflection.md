# Mission Reflection

Object storage is better suited for storing millions of photos because it is designed to handle large amounts of unstructured data such as images, videos, documents, and backups. Unlike traditional block storage, object storage organizes data as objects with metadata and unique identifiers. This makes it easier to manage a large collection of photos and allows storage to scale as the amount of data increases.

Docker made deploying the MinIO storage server easier because I did not have to manually install and configure all of the software and its dependencies. I only needed to run a Docker command that downloaded the MinIO image and created a container. Docker also made it easier to configure the required ports, administrator credentials, and storage server settings in a single command.

A bucket in cloud storage is a container used to organize and store objects. In this laboratory, I created a bucket named `client-photos`, which was used to store a sample uploaded image or file. The bucket provides a logical location where related objects can be managed.

Large enterprise companies can reduce the risk of data loss by using redundancy, replication, backups, and multiple storage servers or locations. If one physical server fails, copies of the data can remain available on other systems. Cloud storage systems can also use durability mechanisms and automated recovery processes to help protect stored data.

My confidence in navigating the Linux command line is growing because I am becoming more comfortable running commands and interpreting their output. In this laboratory, I used Docker commands to deploy and verify MinIO, and I learned how ports and environment variables affect a container. I also gained more experience connecting command-line tasks with a web-based cloud storage interface. Overall, this activity helped me understand how object storage can be deployed and managed using modern cloud-native tools.
