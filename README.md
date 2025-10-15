Lightweight Architecture for Testing a PySpark Project with Jupyter and Docker

Schema of the architecture:

┌────────────────────────────┐
│     Jupyter Notebook       │
│ (pyspark-notebook:3.5.0)   │
│ - Web UI → localhost:8888  │
│ - Shared volumes:          │
│   • ./notebooks            │
│   • ./data                 │
│   • ./output               │
└──────────────┬─────────────┘
               │
     (spark-network bridge)
               │
┌──────────────┴─────────────┐
│        Spark Master        │
│    (bitnami/spark:3.5.0)   │
│ - Web UI → localhost:8080  │
│ - Worker port → 7077       │
└───────────┬───────┬────────┘
            │       │
  ┌─────────┘       └─────────┐
  ▼                           ▼
┌──────────────────┐  ┌──────────────────┐
│  Spark Worker 1  │  │  Spark Worker 2  │
│ (bitnami/spark)  │  │ (bitnami/spark)  │
│ - Connects to     │  │ - Connects to    │
│   spark://master  │  │   spark://master │
└──────────────────┘  └──────────────────┘

