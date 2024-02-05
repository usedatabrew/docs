# Kafka Target Connector

## Introduction

This document provides a detailed guide on setting up the Kafka target connector for the DataBrew project. The Kafka
connector facilitates efficient and reliable streaming of processed data into your Kafka topics, ensuring that your data
pipeline's output is seamlessly integrated into your event streaming platform.

## Requirements

Before setting up the Kafka target connector, ensure you meet the following requirements:

- Access to your Kafka cluster.
- Necessary permissions to produce messages to the Kafka topics.
- Understanding of your Kafka cluster's configuration, including topic setup and partitioning strategy.

### Preparing Your Kafka Cluster

To ensure smooth integration:

- **Topic Configuration**: Ensure that the topics you intend to produce messages to are properly configured in your
  Kafka cluster.
- **Access Control**: Verify that the DataBrew project's user account or service has the required permissions to produce
  messages, and create the desired topics.

## Cloud Setup

This section guides you through setting up the Kafka target connector in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Target Connector Instance**: Follow these steps...
    - Step 1: Choose 'Kafka' from the list of available target connectors.
    - Step 2: Provide the necessary connection details, including your Kafka brokers, authentication details, and target
      topic.
    - Step 3: Configure additional settings like partitioning strategy, key serialization, and value serialization as
      required.
    - (Include screenshots or code snippets if necessary)

## Open Source Setup

| Param                | Type                                    | Description                                                                                                 |
|----------------------|-----------------------------------------|-------------------------------------------------------------------------------------------------------------|
| brokers              | []string                                | Contains a list of brokers Blink will use to stream data to                                                 |
| sasl                 | boolean                                 | Specify if you need to use SASL to connect to the cluster                                                   |
| sasl_password        | string/Env variable                     | Specify only if `sasl` is set to `true`                                                                     |
| sasl_user            | string/Env variable                     | Specify only if `sasl` is set to `true`                                                                     |
| sasl_mechanism       | plain/scramsha256/scramsha512/awsmskiam | Specify only if `sasl` is set to `true`. It select the auth mechanism                                       |
| bind_topic_to_stream | boolean                                 | If you have a multiple streams and you want each stream to push data to the topic with a corresponding name |
| topic_name           | string                                  | Default topic all the messages will be published to. Will be used if `bind_topic_to_stream` is not set      |

Blink config will look as follows:
```yaml
sink:
  driver: kafka
  config:
    brokers:
      - ${KAFKA_BROKER_1}
      - ${KAFKA_BROKER_2}
    sasl: true
    sasl_user: ${SALS_USER}
    sasl_password: ${SALS_PASSWORD}
    sasl_mechanism: plain
    bind_topic_to_stream: false
    topic_name: example
```

## Important Section

In this section, we include essential tips, tricks, and important information related to the Kafka target connector for
the DataBrew project.

- **Data Serialization**: Ensure that the data serialization format used by DataBrew aligns with the deserialization
  process on the Kafka consumer side.
- **Throughput and Performance**: Monitor the throughput and performance of your Kafka producers. Adjust batch size,
  linger time, and buffer memory settings as necessary.
- **Red Panda Support**: While DataBrew primarily supports Apache Kafka, there is potential support for Red Panda (an
  Apache Kafka alternative) for specific use cases. Please contact DataBrew support for more information and guidance on
  this integration.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for setting up the Kafka target
connector for the DataBrew project. By following the steps outlined, you can ensure that your processed data is
efficiently and reliably streamed to your Kafka topics.

For further assistance or queries, please contact [support](mailto:support@databrew.tech).
