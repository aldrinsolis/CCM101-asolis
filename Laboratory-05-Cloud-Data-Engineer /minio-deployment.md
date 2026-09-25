# MinIO Deployment

## 1. Exact Docker Command Used

The following Docker command was used to deploy the MinIO object storage server:

```bash
docker run -d -p 9000:9000 -p 9001:9001 --name minio-server -e "MINIO_ROOT_USER=cloudadmin" -e "MINIO_ROOT_PASSWORD=CloudNova2026!" minio/minio server /data --console-address ":9001"

```

2. Web Console Port
The MinIO Web Console was accessed using port 9001.
```bash
9001

```
3. Bucket Created
The bucket created in the MinIO Web Console was:
```bash
client-photos

```
4. Environment Variables (-e Flags)
The -e flags in the Docker command were used to set environment variables for the MinIO server.
MINIO_ROOT_USER
```bash
-e "MINIO_ROOT_PASSWORD=CloudNova2026!"
