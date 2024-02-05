# AirTable Source Connector 

## Introduction
This document provides a detailed guide on setting up the AirTable source connector for your ETL Cloud project. The AirTable connector facilitates the efficient consumption and integration of data from your AirTable bases into your data pipeline.

## Requirements

Before setting up the AirTable source connector, ensure you meet the following requirements:

- Access to your AirTable account.
- Necessary permissions to read data from your AirTable bases.
- Tables set with a primary key.

### Obtaining AirTable API Key

To connect your AirTable bases with the ETL Cloud project, you need an API key. Follow these steps to obtain your AirTable API key:

1. Log in to your AirTable account.
2. Click on your account icon at the top-right corner and select 'Account' from the dropdown menu.
3. Under the 'API' section, find the 'Generate API key' button and click on it.
4. Copy the generated API key and store it securely.

**Note**: Treat your API key like a password. Do not share it publicly or with unauthorized users.


## Cloud Setup

This section guides you through setting up the AirTable source connector in the cloud.

### Setting up in Cloud
1. **Access DataBrew Cloud Platform**: Navigate to your cloud platform [https://app.databrew.tech](https://app.databrew.tech)
2. **Create a New Source Connector Instance**: Follow these steps...
    - Step 1: Choose 'AirTable' from the list of available source connectors.
    - Step 2: Provide the necessary connection details, including the API key obtained from AirTable.
    - Step 3: Select the specific AirTable base and table you wish to integrate.
    - (Include screenshots or code snippets if necessary)

**Important**: Ensure that the tables you select have a designated primary key, as this is crucial for the proper functioning of the connector.

## Open Source Setup
Make sure you have `Blink` installed or Docker image pulled. 
If not - go to [Installation section](Installation.md)

### Specify your tables schema
Describe your AirTable tables schema in the `service` section for Blink

```yaml
service:
  id: 123
  stream_schema:
    - stream: 23j42j4.taxi_rides
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

> Please, pay attention to the stream name. It's a combination of AirTable `BaseId` and the `Table` name itself

### Specify source
Now you can easily specify source in your Blink configuration
```yaml
source:
  driver: airtable
  config:
    api_key: ${API_KEY_ENV_NAME}
```

## Important

In this section, we include essential tips, tricks, and important information related to the AirTable source connector.

- **Primary Key Requirement**: Ensure that each table in your AirTable base has a designated primary key. This is crucial for the connector to accurately track and sync individual records.
- **API Rate Limits**: Be mindful of AirTable's API rate limits to avoid interruptions in data syncing. Plan your data integration strategy accordingly.
- **Data Types**: Verify that the data types in your AirTable columns are compatible with your ETL pipeline's schema.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for the AirTable source connector. 
By following the steps outlined, you can seamlessly integrate your AirTable data into your ETL Cloud project.

For further assistance or queries, please contact [support](mailto:support@databrew.tech)..