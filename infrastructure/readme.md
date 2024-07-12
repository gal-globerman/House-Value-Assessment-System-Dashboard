# Infrastructure Repository

## Purpose
Contains code to run external services.

## Services

### 1. Minio (S3-like storage)
**Required Environment Variables**
```env
MINIO_ROOT_USER=<user>
MINIO_ROOT_PASSWORD=<password>
S3_ACCESS_KEY_ID=<access-key>
S3_SECRET_KEY=<secret-key>
S3_API_PORT=<api port>
S3_WEB_UI_PORT=<web ui port>
```

**Startup**
```bash
docker-compose --env-file .env -f minio/docker-compose.yml up -d
```

To ensure proper operation of DVC and MLFlow, you need to create the corresponding buckets through the Minio web interface:
```env
DVC_BUCKET=<ENTER YOUR VALUE>
MLFLOW_BUCKET=<ENTER YOUR VALUE>
```

### 2. MLflow, PostgreSQL, PgAdmin
**Required Environment Variables**
```env
SERVER_HOST=<ENTER YOUR VALUE>
SERVER_SCHEMA=<ENTER YOUR VALUE>
S3_ACCESS_KEY=<ENTER YOUR VALUE>
S3_SECRET_KEY=<ENTER YOUR VALUE>
S3_API_PORT=<ENTER YOUR VALUE>
MLFLOW_BUCKET=<ENTER YOUR VALUE>
POSTGRES_DB=<ENTER YOUR VALUE>
POSTGRES_USER=<ENTER YOUR VALUE>
POSTGRES_PASSWORD=<ENTER YOUR VALUE>
PGADMIN_EMAIL=<ENTER YOUR VALUE>
PGADMIN_PASSWORD=<ENTER YOUR VALUE>
```

**Startup**
```bash
docker-compose --env-file .env -f mlflow/docker-compose.yml up -d
```

### 3. Prometheus, Grafana, Loki
**Startup**
```bash
docker-compose -f monitoring/docker-compose.yml up -d
```
