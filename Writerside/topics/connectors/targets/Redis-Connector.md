# Redis Target Connector

## Introduction

This document provides a detailed guide on setting up the Redis target connector for the DataBrew project. The Redis connector allows for efficient and flexible storage of processed data, ensuring that your data pipeline's output is securely persisted or cached in your Redis data store.

## Requirements

Before setting up the Redis target connector, ensure you meet the following requirements:

- Access to your Redis instance or Redis cloud service.
- Necessary permissions to write data into the Redis data store.
- Understanding of Redis data structures and best practices for data storage.

### Preparing Your Redis Environment

To ensure smooth integration:

- **Data Structure Design**: Understand and plan the Redis data structures (e.g., strings, hashes, lists, sets, sorted sets) to use for storing your processed data.
- **Security & Access Control**: Verify that the DataBrew project's user account or service has the required permissions to write data to the desired keys in Redis.

## Cloud Setup

This section guides you through setting up the Redis target connector in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Target Connector Instance**: Follow these steps...
    - Step 1: Choose 'Redis' from the list of available target connectors.
    - Step 2: Provide the necessary connection details, including your Redis server URL, authentication details, and target data structure configurations.
    - Step 3: Configure additional settings like key naming conventions, expiration policies, and data serialization formats, as required.
    - (Include screenshots or code snippets if necessary)

## Open Source Setup
Make sure you have `Blink` installed or Docker image pulled.
If not - go to [Installation section](Installation.md)

### Specify destinations
Blink configuration should look as follows:

```yaml
sink:
  driver: redis
  config:
    redis_addr: ${REDIS_ADDR} # redis://redishost:2313
    redis_password: ${REDIS_PASSWORD}
    # custom_namespace can't be used alongside with NamespaceByStream, only one of the
    # Options should be provided.
    # In case provided both - namespace by stream will be used
    custom_namespace: my_namespace
    namespace_by_stream: false
    key_prefix: optional_prefix_for_keys
    set_with_ttl: 10 # seconds for key TTL 
```


## Important Section

In this section, we include essential tips, tricks, and important information related to the Redis target connector for the DataBrew project.

- **Data Serialization**: Ensure that the data serialization format used by DataBrew aligns with the deserialization process when reading the data from Redis.
- **Key Management**: Plan and manage your key space in Redis to prevent collisions and ensure efficient data retrieval.
- **Performance and Scalability**: Monitor your Redis instance's performance and consider best practices for scaling, such as using Redis clustering or sharding for high-load scenarios.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for setting up the Redis target connector for the DataBrew project. By following the steps outlined, you can ensure that your processed data is efficiently and reliably stored or cached in your Redis data store.

For further assistance or queries, please contact [support](mailto:support@databrew.tech).
