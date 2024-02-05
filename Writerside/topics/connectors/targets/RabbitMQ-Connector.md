# RabbitMQ Target Connector

## Introduction

This document provides a detailed guide on setting up the RabbitMQ target connector for the DataBrew project. The RabbitMQ connector facilitates efficient and reliable queuing of processed data into your RabbitMQ exchanges and queues, ensuring that your data pipeline's output is seamlessly integrated into your message broker system.

## Requirements

Before setting up the RabbitMQ target connector, ensure you meet the following requirements:

- Access to your RabbitMQ server or RabbitMQ cloud service.
- Necessary permissions to publish messages to the RabbitMQ exchanges and queues.
- Understanding of your RabbitMQ server's configuration, including exchange types, queue bindings, and routing keys.

### Preparing Your RabbitMQ Environment

To ensure smooth integration:

- **Exchange and Queue Configuration**: Ensure that the exchanges and queues you intend to publish messages to are properly configured in your RabbitMQ server.
- **Security & Access Control**: Verify that the DataBrew project's user account or service has the required permissions to publish messages to the desired exchanges and queues.

## Cloud Setup

This section guides you through setting up the RabbitMQ target connector in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Target Connector Instance**: Follow these steps...
    - Step 1: Choose 'RabbitMQ' from the list of available target connectors.
    - Step 2: Provide the necessary connection details, including your RabbitMQ server URL, authentication details, target exchange, and routing key.
    - Step 3: Configure additional settings like exchange type, queue durability, and message persistence, as required.
    - (Include screenshots or code snippets if necessary)

## Open Source Setup
Make sure you have `Blink` installed or Docker image pulled.
If not - go to [Installation section](Installation.md)

### Specify destinations
Blink configuration should look as follows:

```yaml
sink:
  driver: rabbitmq
  config:
    url: ${RABBITMQ_URI} # env variable with all the credentials like: amqp://user:pass@host:10000/vhost
    exchange_name: name_of_the_exchange
    routing_key: optional_name_of_the_routing_key
```

## Important Section

In this section, we include essential tips, tricks, and important information related to the RabbitMQ target connector for the DataBrew project.

- **Message Serialization**: Ensure that the message serialization format used by DataBrew aligns with the deserialization process on the RabbitMQ consumer side.
- **Exchange and Queue Design**: Understand and plan your exchange and queue architecture to ensure proper message routing, durability, and performance.
- **Monitoring and Reliability**: Implement monitoring on your RabbitMQ server to track message delivery and queue health. Consider setting up clustering and high availability for critical data streams.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for setting up the RabbitMQ target connector for the DataBrew project. By following the steps outlined, you can ensure that your processed data is efficiently and reliably queued into your RabbitMQ system.

For further assistance or queries, please contact [support](mailto:support@databrew.tech).
