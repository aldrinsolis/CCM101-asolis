# Cloud Storage Types Research

## Comparison of Cloud Storage Types

| Storage Type | Description | Primary Use Case | Cloud Provider Example |
|---|---|---|---|
| Block Storage | Stores data in fixed-size blocks that can be accessed individually. | Best for virtual machines, databases, and applications that require high-performance storage. | AWS EBS |
| File Storage | Stores data as files organized in folders and directories. Multiple users or applications can access the same files. | Best for shared files, documents, and applications that need a traditional file system. | AWS EFS |
| Object Storage | Stores data as objects together with metadata and a unique identifier. | Best for images, videos, backups, documents, and large amounts of unstructured data. | AWS S3 |

## Client Recommendation

Object Storage is the best choice for storing user-uploaded images because it is designed to handle large amounts of unstructured data such as photos. It can store and retrieve files efficiently while allowing the storage system to scale as the number of uploaded images increases.
