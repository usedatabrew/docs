# PostgreSQL Source Connector

## Introduction

This document provides a detailed guide on setting up the PostgreSQL source connector with CDC (Change Data Capture) mode using Logical Replication for the DataBrew project. This setup allows for real-time data synchronization and ensures that your data pipeline is always up-to-date with the latest changes in your PostgreSQL database.

### Target Connector
If you are looking for a target connector for PostgreSQL you can see the doc here: [Target PostgreSQL Connector](Postgres-Connector.md)

## Requirements

Before setting up the PostgreSQL source connector, ensure you meet the following requirements:

- Access to your PostgreSQL database.
- Necessary permissions to modify database parameters and manage replication slots.
- PostgreSQL version 9.4 or higher (logical replication is supported from 9.4 onwards).

### Configuring PostgreSQL for Logical Replication

To use CDC mode with Logical Replication, you need to set the appropriate WAL (Write-Ahead Logging) level. The process varies depending on your setup:

#### Standard PostgreSQL Installation

For a standard installation, modify the `postgresql.conf` file:

1. Open the `postgresql.conf` file in your preferred text editor.
2. Locate the `wal_level` parameter and set it to `logical`: `wal_level = logical`
3. Save the file and restart your PostgreSQL instance to apply the changes.

#### AWS RDS

For PostgreSQL on AWS RDS:

1. Open the RDS console.
2. Navigate to `Parameter groups`.
3. Select the parameter group associated with your PostgreSQL instance.
4. Edit the parameters and set `rds.logical_replication` to `1` and `wal_level` to `logical`.
5. Save the changes and wait for them to be applied.

#### Azure Database for PostgreSQL

For PostgreSQL on Azure:

1. Open the Azure portal.
2. Navigate to your PostgreSQL database server.
3. Select `Server parameters`.
4. Find the `wal_level` parameter and set it to `logical`.
5. Save the changes and restart your server if required.

> **Note**: Changing the WAL level to `logical` is crucial for enabling logical replication and allowing the DataBrew project to capture change data. Ensure your environment allows the modifications and plan for any necessary downtime or maintenance window.

## Cloud Setup

This section guides you through setting up the PostgreSQL source connector with CDC mode in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Source Connector Instance**: Follow these steps...
- Step 1: Choose 'PostgreSQL' from the list of available source connectors.
- Step 2: Provide the necessary connection details, including your database credentials and the host address.
- Step 3: Configure the connector to use CDC mode with Logical Replication.
- (Include screenshots or code snippets if necessary)

## Open Source Setup
Make sure you have `Blink` installed or Docker image pulled.
If not - go to [Installation section](Installation.md)

### Specify your tables schema
Describe your PostgreSQL tables schema in the `service` section for Blink

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

### Specify source
Now you can set PostgreSQL config for source. Follow the example below:

```yaml
source:
  driver: postgres_cdc
  config:
    host: ${DATABASE_HOST}
    slot_name: my_resplication_slot_name # Or random will be created if not specified
    user: ${DATABASE_USER}
    database: ${DATABASE_NAME}
    password: ${DATABASE_PASSWORd}
    port: ${DATABASE_PORT}
    schema: public
    stream_snapshot: true # Set true if you need to stream existing data first
    snapshot_batch_size: 5000 # This param affects the memory consumption of the blink instance.
```

## Important Section

In this section, we include essential tips, tricks, and important information related to the PostgreSQL source connector with CDC mode for the DataBrew project.

- **Monitor WAL Size**: Logical replication can increase the size of your WAL. Monitor disk space and manage old WAL segments appropriately.
- **Replication Slot**: Ensure that the replication slot is created for the DataBrew connector and is active. Inactive slots can lead to increased disk usage due to uncleared WAL segments.
- **Database User Permissions**: The user used by DataBrew to connect to your PostgreSQL database should have the necessary permissions to read the tables you want to sync and to manage replication slots.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for setting up the PostgreSQL source connector with CDC mode using Logical Replication for the DataBrew project. By following the steps outlined, you can ensure real-time data synchronization and maintain an up-to-date data pipeline.

For further assistance or queries, please contact [support](mailto:support@databrew.tech).
