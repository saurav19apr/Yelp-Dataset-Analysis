# Yelp Dataset Analysis
## Project Overview
This project focuses on analyzing the Yelp Dataset using Spark and Parquet format on Azure Databricks. The primary objective is to showcase the efficiency and simplicity of using Azure Databricks for the ELT/ETL process, making it an excellent tool for Data Engineers.

Below is a representation of the project workflow.
![analyse-yelp-dataset-with-spark-parquet-format-on-azure-databricks](https://github.com/user-attachments/assets/e67e81fc-e697-4fd9-bbc7-b89020299d1d)

### Data Source
![Screenshot 2024-09-10 152505](https://github.com/user-attachments/assets/10c1f4c1-63b1-4e42-98f3-5b5fb2d6e444)
Yelp, the renowned platform for local business reviews and reservations, has opened its vast data treasury to the public. This San Francisco-based company's initiative invites researchers, data scientists, and curious minds to explore and analyze millions of user-generated reviews and business information.
The Yelp Dataset Challenge offers a unique opportunity to uncover hidden insights and trends in local business data. Whether you're into natural language processing, sentiment analysis, or discovering market patterns, this dataset provides a rich playground for innovation and discovery.

## Azure
Azure is Microsoft's cloud computing platform. It provides a wide range of services including:

1)Computing power for running applications.

2)Storage and databases.

3)Networking capabilities.

4)Artificial intelligence and machine learning tools.

5)Internet of Things (IoT) services.

6)DevOps and development tools.

Azure allows businesses to build, run, and manage applications across multiple clouds and on-premises without having to maintain physical hardware. It's designed to be flexible, scalable, and cost-effective, supporting various programming languages and frameworks.

We'll utilize Databricks, Azure Storage, and Azure Data Factory for this project.


# Getting Started 

## Step 1 Creating Azure Resource Group
An Azure Resource Group acts as a container that organizes and manages related resources for a project. It allows you to group various Azure services and components together, ensuring they're logically separated from resources belonging to other projects. This grouping simplifies management, deployment, and access control. Additionally, Resource Groups enable you to monitor costs and apply policies across all resources within the group, enhancing both organization and efficiency in your Azure environment.


https://github.com/user-attachments/assets/aa8ccb72-9dc8-4b3b-b8c2-d17d5b9a8666



## Step 2 Creating Azure Storage 
Azure Storage is a scalable cloud storage service provided by Microsoft Azure. It offers secure, durable, and highly available storage for various data types, including blobs, files, queues, and tables. Within Azure Storage, we'll establish containers that serve as repositories for our stored data. These containers act as the actual storage units where our information will reside.


https://github.com/user-attachments/assets/7095d925-76f9-4874-b35b-6d5d6fdd2d18

## Step 2.1 Creating Container
Having set up our Azure Storage account for this project, we can now move forward with creating a container. This container will serve as the dedicated space for storing the Yelp dataset. Once the data is in place, we'll be able to perform various operations and analyses on it, leveraging the capabilities of Azure Storage and other integrated services.


https://github.com/user-attachments/assets/af50c176-9fb2-450d-bd73-ac47c2ed0bf8


## Step 3 Initializing Azure Data Fcatory 
Azure Data Factory is a fully managed, serverless data integration solution used for constructing ETL (Extract, Transform, Load) and ELT (Extract, Load, Transform) processes. It allows you to create data-driven workflows for orchestrating and automating data movement and data transformation.
Key features include:

1)Data ingestion from various sources, both on-premises and cloud-based.

2)Data transformation using compute services like Azure HDInsight, Azure Databricks, and SQL Server Integration Services.

3)Workflow orchestration and scheduling.

4)Monitoring and management of data pipelines.

5)Integration with other Azure services and external tools.


https://github.com/user-attachments/assets/6b3b2351-478a-4a8b-b303-6aa98950c818

## Step 4 Creating Pipeline
After setting up Azure Data Factory, our next step is to create the initial pipeline. For this pipeline, we'll employ the "Copy Data" activity. This activity will facilitate the transfer of data from the original file in our container to a designated source file.
The purpose of this step is twofold:

1)It preserves the original dataset in its unaltered state, which can be crucial for data integrity and future reference.

2)It creates a separate working copy that we can manipulate and transform for our specific analysis tasks.

This approach ensures we always have access to the pristine, original data for other potential tasks or if we need to revert changes. It's a best practice in data management that provides flexibility and safeguards against accidental modifications to the primary dataset.


https://github.com/user-attachments/assets/cd5e2a9d-70b2-48f4-bf22-401898f1ff05

## Step 5 Launching Azure Databricks
Azure Databricks is a unified data analytics platform that combines the best of Databricks and Microsoft Azure. It provides a fully managed, cloud-based Big Data and machine learning platform that enables teams to collaborate on shared projects.
Key features include:

1)Apache Spark-based processing for big data analytics.

2)Interactive workspaces for data scientists, data engineers, and business analysts.

3)Support for multiple languages including Python, Scala, R, and SQL.

4)Seamless integration with other Azure services.

5)Built-in security and compliance features.

6)Automated cluster management and scaling.



https://github.com/user-attachments/assets/8dbbd6b7-b393-4216-9981-eca867dcfffe



## Step 6 Creating Data Bricks Clusture
Databricks clusters are groups of computers that work together to process our data and run computational tasks.

The cluster configuration shows 16GB of memory and 4 cores per node. As the number of worker nodes increases, the total number of cores and overall computational power will grow proportionally. However, for smaller projects like this one, even a single node with 4 cores may be sufficient.
It's important to note that if more computational power is needed—whether through increased cores or additional nodes—you may need to request an increase in your Azure quota. Azure quotas limit the number of resources you can provision, and they're designed to prevent accidental over-consumption of resources.
The key points to remember are:

1)Cluster power scales with the number of worker nodes.

2)Small projects can often run efficiently on minimal configurations.

3)Azure quotas may limit your ability to scale up, so plan accordingly.

This approach allows for flexibility in resource allocation, enabling you to balance performance needs with cost considerations for your specific project requirements.



https://github.com/user-attachments/assets/55a84f1d-4cff-4858-b816-cd5fe018a661

## Step 7 Analysis
With the data transfer from the target to the source file complete and Databricks fully configured, we now move to the final phase: data preparation. This crucial step readies the data for various applications, such as analysis or use in machine learning models. The initial and most important task in this process is to establish a connection between our data source and the notebook using Spark, as demonstrated in the instructional video.


https://github.com/user-attachments/assets/f8209005-ea9b-494c-a296-ef7bd67382f9


Now that we can access data from Azure Storage, we need to convert the JSON files into Parquet format. This conversion is necessary because Parquet offers several advantages:

1)It's a columnar storage format, allowing for more efficient compression and faster query performance.

2)It enforces schema, improving data consistency.

3)It's widely compatible with big data processing tools like Spark.

4)It significantly reduces storage space and I/O operations, optimizing overall data processing efficiency.

![Screenshot 2024-09-24 133507](https://github.com/user-attachments/assets/32fb4fb7-709a-4fe6-98c9-b7ace9342da9)


Once the conversion to Parquet is complete, we can begin analyzing the data. We'll start by determining the number of records in our dataset. Then, we'll partition the data, which is crucial for several reasons:

1)Improved query performance: Partitioning allows for faster data retrieval by limiting the amount of data scanned.

2)Efficient processing: It enables parallel processing, speeding up operations on large datasets.

3)Better organization: Partitioning logically groups related data, making it easier to manage and understand.

4)Optimized storage: It can lead to more efficient data storage and reduced costs, especially in cloud environments.

Partitioning is particularly important when dealing with large datasets, as it significantly enhances both performance and manageability.
![Screenshot 2024-09-24 133600](https://github.com/user-attachments/assets/e1770eeb-4b12-4a44-93cd-87c6bb8cef18)


The PySpark function createOrReplaceTempView allows us to create a temporary view of a DataFrame, enabling us to use SQL commands on the data. This function is particularly useful for several reasons:

1)SQL familiarity: It allows data analysts and engineers to use familiar SQL syntax to query and manipulate data in Spark DataFrames.

2)Complex queries: SQL often provides a more intuitive way to express complex data transformations and aggregations.

3)Interoperability: It bridges the gap between DataFrame operations and SQL operations, allowing you to switch between the two as needed.

4)Performance: Spark can optimize SQL queries efficiently, potentially leading to better performance for certain operations.

5)Simplification: For large datasets, SQL queries can sometimes be more concise and easier to understand than equivalent DataFrame operations.

By using createOrReplaceTempView, we create a named view that persists only for the duration of the Spark session, making it easier to perform operations on large datasets using well-known SQL commands.

![Screenshot 2024-09-24 134334](https://github.com/user-attachments/assets/2963b7e7-efd1-4c6d-8755-2f43d4dd34da)


# Conclusion

In conclusion, this project serves as a comprehensive demonstration of modern data engineering practices, leveraging powerful tools like Databricks, Azure Storage, and Azure Data Factory. We've successfully transformed raw, unstructured data into a refined, analysis-ready format, showcasing the critical role of data engineering in today's data-driven world. By bridging the gap between raw data and actionable insights, we've laid the groundwork for advanced analytics, machine learning, and AI applications. This repository not only contains the necessary code and data samples but also stands as a testament to the potential of well-engineered data. It invites further exploration and serves as a springboard for innovative data solutions across various domains. Whether you're a seasoned data professional or an aspiring analyst, this project offers valuable insights into the art and science of preparing data for the challenges of tomorrow.
