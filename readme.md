# ML Project for Real Estate Price Prediction

## System Architecture

![System Architecture](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/architecture-1.png)


## Research
- Data is versioned using DVC
- A CLI script is created for each data processing stage
- Experiments are logged using MLflow


Data Processing DAG
```mermaid
flowchart TD                       
        node1["add_coordinates"]   
        node2["clean_data"]        
        node3["download_amenities"]
        node4["download_raw_data"] 
        node5["finalize_data"]     
        node1-->node5              
        node2-->node1              
        node2-->node5              
        node3-->node5              
        node4-->node2
```

![Buckets in S3 storage](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/minio-1.png)
![Experiments](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/mlflow-1.png)
![Model Artifacts](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/mlflow-3.png)

## Infrastructure
- Minio (buckets for DVC and MLflow)
- MLflow, PostgreSQL, PgAdmin
- Prometheus, Loki, Grafana

![Monitoring in Grafana](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/grafana-1.png)


## Backend, Model Serving
- FastAPI, Catboost
- Loads the current model from Model Registry
- Sends logs to Loki
- Provides metrics for Prometheus

![Swagger Documentation](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/swagger-1.png)


## Frontend
- Vite, React, Maplibre, MUI
- Provides users with a map interface
- Apartment distribution analytics
- Price prediction based on house and apartment characteristics

![Analysis](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/application-3.png)
![Forecast by Characteristics](https://github.com/gal-globerman/House-Value-Assessment-System-Dashboard/blob/master/visual/application-5.png)