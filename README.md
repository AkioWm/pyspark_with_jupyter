Lightweight Architecture for Testing a PySpark Project with Jupyter and Docker

Schema of the architecture:

graph TD
    A[Jupyter Notebook 🧠<br>(pyspark-notebook:3.5.0)]:::jupyter
    B[Spark Master 🧩<br>(bitnami/spark:3.5.0)]:::master
    C[Spark Worker 1 ⚙️<br>(bitnami/spark:3.5.0)]:::worker
    D[Spark Worker 2 ⚙️<br>(bitnami/spark:3.5.0)]:::worker

    %% Connections
    A -->|Submits PySpark Jobs| B
    B -->|Distributes Tasks| C
    B -->|Distributes Tasks| D

    %% Styling
    classDef jupyter fill:#f6f8fa,stroke:#0366d6,stroke-width:2px,color:#000,font-weight:bold;
    classDef master fill:#fff8e1,stroke:#ffb300,stroke-width:2px,color:#000,font-weight:bold;
    classDef worker fill:#e8f5e9,stroke:#388e3c,stroke-width:2px,color:#000,font-weight:bold;

    %% Notes
    subgraph Network 🌐 spark-network
        A
        B
        C
        D
    end

