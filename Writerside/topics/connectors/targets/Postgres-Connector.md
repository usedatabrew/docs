# PostgreSQL Target Connector

## Introduction

This document provides a detailed guide on setting up the PostgreSQL target connector for the DataBrew project. The PostgreSQL connector allows for efficient and reliable storage of processed data, ensuring that your data pipeline's output is securely persisted in your PostgreSQL database.

## Requirements

Before setting up the PostgreSQL target connector, ensure you meet the following requirements:

- Access to your PostgreSQL database.
- Necessary permissions to write data into the PostgreSQL tables.
- Understanding of the data schema and any constraints within your PostgreSQL database.

### Preparing Your PostgreSQL Database

To ensure smooth integration:

- **Permissions**: Verify that the DataBrew project's user account has write access to the desired tables.
- **Schema Design**: DataBrew will automatically create the tables needed on a target database. Please, make sure that user, given to DataBrew has the permission to create tables in schema 

## Cloud Setup

This section guides you through setting up the PostgreSQL target connector in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Target Connector Instance**: Follow these steps...
    - Step 1: Choose 'PostgreSQL' from the list of available target connectors.
    - Step 2: Provide the necessary connection details, including your database host, database name, user, and password.
    - Step 3: Configure the connector by specifying the target tables and any necessary column mappings or transformations.
    - (Include screenshots or code snippets if necessary)

## Open Source Setup

Blink config for PostgreSQL target looks as follows:
```yaml
sink:
  driver: postgres
  config:
    host: ${DATABASE_HOST}
    user: ${DATABASE_USER}
    password: ${DATABASE_PASSWORD}
    port: ${DATABASE_PORT}
    schema: public
    database: ${DATABASE_NAME}
```

## Important Section

In this section, we include essential tips, tricks, and important information related to the PostgreSQL target connector for the DataBrew project.

- **Data Consistency**: Ensure that the data written to your PostgreSQL database maintains consistency with the expected schema or data model.
- **Performance Optimization**: Utilize PostgreSQL's performance optimization features, such as indexing and proper query design, to ensure efficient data storage operations.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for setting up the PostgreSQL target connector for the DataBrew project. By following the steps outlined, you can ensure that your processed data is efficiently and reliably stored in your PostgreSQL database.

For further assistance or queries, please contact [support](mailto:support@databrew.tech).
