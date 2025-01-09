# Traffic Data Medallion Architecture and Pipeline Orchestration



## 🚦 Project Overview
This project implements a **Medallion Architecture** for processing and analyzing traffic data using Databricks. The pipeline is designed to handle data ingestion, transformation, and loading incrementally with the help of Databricks' **Autoloader**. The orchestration of the entire pipeline is managed through **workflows** in Databricks.

---

## 🏗️ Architecture Design: Medallion Layers

### 1. **Bronze Layer**
- **Purpose**: Acts as the raw data storage layer, ingesting data in its original format.
- **Implementation**: 
  - Data is loaded from external sources into the Bronze layer using Databricks **Autoloader** for efficient incremental loading.
  - Ensures schema inference and automatic detection of new files for seamless updates.

### 2. **Silver Layer**
- **Purpose**: Cleanses and transforms data to create a structured, analytics-ready dataset.
- **Traffic Transformations**:
  - Data deduplication and validation.
  - Enhancements to data quality through column transformations and filtering.
- **Roads Transformations**:
  - Specific transformations for road-related data to normalize and harmonize attributes.

### 3. **Gold Layer**
- **Purpose**: Stores final aggregated data optimized for analytics and reporting.
- **Implementation**:
  - Final transformations, aggregations, and loading into analytics-friendly tables.

---

## ⚙️ Pipeline Orchestration
- **Tool**: Databricks Workflows
- **Workflow Features**:
  - Sequential orchestration of notebooks, ensuring dependencies between layers are maintained.
  - Robust handling of incremental updates across all medallion layers.
  - Monitoring and alerting mechanisms to ensure data integrity.

---

## 🛠️ Key Features
1. **Incremental Data Loading**:
   - Leveraged Databricks **Autoloader** to support real-time, scalable, and efficient data ingestion.
   - Eliminates the need for batch processing, enabling continuous updates.
   
2. **Reusable Common Functions**:
   - Created reusable code modules in the `Common` notebook to streamline the pipeline and avoid redundancy.
   - Functions for logging, error handling, and utilities.

3. **Data Transformations**:
   - Traffic and road data processed in Silver layer for consistency.
   - Final aggregated metrics calculated in Gold layer for easy visualization and reporting.

---

## 📂 Project Structure
### Notebooks:
1. **01. Project Setup**: Initial configuration and environment setup.
2. **02. Load to Bronze**: Data ingestion into the Bronze layer using Autoloader.
3. **03. Silver - Traffic Transformations**: Traffic-specific data cleansing and transformations.
4. **04. Common**: Reusable utility functions for the pipeline.
5. **05. Silver - Roads Transformation**: Processing and transformation of road-related data.
6. **06. Gold - Final Transformations and Loading**: Final computations and loading into the Gold layer.

---

## 🚀 How to Use
1. **Setup Environment**:
   - Clone the repository and set up the necessary Databricks workspace.
   - Ensure the source data is available and accessible for Autoloader.

2. **Run the Workflow**:
   - Use Databricks Workflows to orchestrate the pipeline. Configure the workflow to execute the notebooks in the specified sequence.

3. **Monitor Pipeline**:
   - Monitor the workflow for successful execution and handle any failures using the logs.

---

## 🤝 Contributing
Contributions are welcome! If you have suggestions for improvement, feel free to submit a pull request.

Jasvinder Singh

