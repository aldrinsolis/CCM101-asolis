# MinIO Deployment

## Docker Command

The following Docker command was used to deploy the MinIO object storage server:

```bash
docker run -d -p 9000:9000 -p 9001:9001 --name minio-server -e "MINIO_ROOT_USER=cloudadmin" -e "MINIO_ROOT_PASSWORD=CloudNova2026!" minio/minio server /data --console-address ":9001"

docker ps

9001

client-photos

-e "MINIO_ROOT_USER=cloudadmin"

-e "MINIO_ROOT_PASSWORD=CloudNova2026!"

-p 9000:9000
-p 9001:9001


