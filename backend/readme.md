# Model Serving Service

## Description
This service allows for predicting apartment prices within the city of Perm.

When the application starts, the current model is loaded from the MLflow Model Registry.

There are two endpoints for predictions: one using an address and the other using the house's coordinates. If the first endpoint is used, a token for the Geoapify service is required.

## Startup

### Required Environment Variables
```env
GEOAPIFY_TOKEN=<GEOAPIFY_TOKEN>
MLFLOW_TRACKING_URI=<TRACKING_URI>
MLFLOW_S3_ENDPOINT_URL=<S3_ENDPOINT_URL>
AWS_ACCESS_KEY_ID=<ACCESS_KEY>
AWS_SECRET_ACCESS_KEY=<SECRET>
MODEL_NAME=<MODEL_NAME>
MODEL_VERSION=<MODEL_VERSION>
DISTRICTS_GEOJSON_PATH=src/static/perm_district.json
AMENITY_DIR_PATH=src/static/amenity
LOGGING_URL=http://localhost:3100/loki/api/v1/push
```
### Deployment Using Docker Compose
```bash
docker-compose up -d
```
For local development, use docker-compose.local.yaml.
