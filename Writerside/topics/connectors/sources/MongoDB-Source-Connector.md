# MongoDB Source Connector

## Introduction

This document provides a detailed guide on setting up the MongoDB source connector for the DataBrew project. The MongoDB connector allows for efficient data integration from MongoDB collections into your DataBrew data pipeline, ensuring a seamless data flow from your MongoDB databases.

## Requirements

Before setting up the MongoDB source connector, ensure you meet the following requirements:

- Access to your MongoDB database.
- Necessary permissions to read data from the MongoDB collections intended for use in your pipeline.
- Understanding of MongoDB's data model and query language to accurately configure the data extraction.

### Preparing Your MongoDB Database

To ensure smooth integration:

- **Indexing**: Ensure proper indexing on your collections to optimize query performance.
- **User Permissions**: Create a database user for the DataBrew project with read access to the necessary collections.

## Cloud Setup

This section guides you through setting up the MongoDB source connector in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Source Connector Instance**: Follow these steps...
    - Step 1: Choose 'MongoDB' from the list of available source connectors.
    - Step 2: Provide the necessary connection details, including your MongoDB host, database name, and credentials.
    - Step 3: Configure the connector by specifying the collections and any query filters if required.
    - (Include screenshots or code snippets if necessary)

## Open Source Setup
Describe your MongoDB collections schema in the `service` section for Blink

> Important to know that DataBrew will not stream message that don't match the provided schema

```yaml
service:
  id: 123
  stream_schema:
    - stream: taxi_rides # stream is a name of the table. You can have a multiple tables streamed at the same time
      columns:
        - name: log_id
          databrewType: Int32
          nativeConnectorType: integer
          pk: true
          nullable: false
        - name: timestamp
          databrewType: String
          nativeConnectorType: varchar
          pk: false
          nullable: true
        - name: driver_id
          databrewType: Int32
          nativeConnectorType: numeric
          pk: false
          nullable: false
```

## Specify source
To specify MongoDB source in Blink you have to add the following yaml to the config file

```yaml
source:
  driver: mongo_stream
  config:
    uri: ${DATABASE_URI} # Full uri with credentials to the server
    database: ${DATABASE_NAME} # Name of the database
    stream_snapshot: true # Set this to true if you need to stream existing data first
```

## Important Section

In this section, we include essential tips, tricks, and important information related to the MongoDB source connector for the DataBrew project.

- **Data Types and Schema**: MongoDB is schema-less, which can lead to data type inconsistencies. Ensure that the data types in your collections align with your pipeline's expectations.
- **Change Streams**: If leveraging MongoDB change streams for real-time data capture, ensure your MongoDB instance supports this feature and it's properly configured.
- **Resource Utilization**: Monitor your MongoDB instance's performance and resource utilization, as heavy queries from the data pipeline can impact overall database performance.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for setting up the MongoDB source connector for the DataBrew project. By following the steps outlined, you can effectively integrate your MongoDB data into your ETL pipeline.

For further assistance or queries, please contact (Support Contact Information).
