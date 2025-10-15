Lightweight Architecture for Testing a PySpark Project with Jupyter and Docker

Schema of the architecture:

                        🧠  Jupyter Notebook
                   (jupyter/pyspark-notebook:3.5.0)
                  ───────────────────────────────────
                    • Web UI → http://localhost:8888
                    • Shared volumes:
                      ./notebooks, ./data, ./output
                               │
                               │  (spark-network)
                               ▼
                      🧩  Spark Master
                   (bitnami/spark:3.5.0)
                  ───────────────────────────────────
                    • Web UI → http://localhost:8080
                    • Worker port → 7077
                    ┌──────────────┬──────────────┐
                    │                             │
                    ▼                             ▼
            ⚙️ Spark Worker 1               ⚙️ Spark Worker 2
            (bitnami/spark:3.5.0)           (bitnami/spark:3.5.0)
                → Connected to spark://spark-master:7077



