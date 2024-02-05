# WebSocket Source Connector

## Introduction

This document provides a comprehensive guide on setting up the WebSocket source connector for the DataBrew project.
The WebSocket connector enables real-time data streaming from your WebSocket server into the DataBrew data pipeline.

### Target Connector
If you are looking for a target connector for WebSockets you can see the doc here: [Target WebSocket Connector](WebSockets-Connector.md)

> It's crucial to understand that the WebSocket connector supports only a single stream and requires a consistent data format throughout the message flow.

## Requirements

Before setting up the WebSocket source connector, ensure you meet the following requirements:

- Access and control over your WebSocket server.
- Understanding of the data schema emitted by your WebSocket server.
- Ensure that the WebSocket server is configured to maintain a consistent data format for every message.

### Data Consistency

To prevent pipeline breaks, confirm that:

- The WebSocket server emits messages in a consistent format.
- No changes are made to the message schema or data format during streaming.

## Cloud Setup

This section guides you through setting up the WebSocket source connector in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Source Connector Instance**: Follow these steps...
    - Step 1: Choose 'WebSocket' from the list of available source connectors.
    - Step 2: Provide the necessary connection details, including the WebSocket server URL and any required headers or authentication details.
    - Step 3: Specify the single stream that the connector should subscribe to.
    - (Include screenshots or code snippets if necessary)

> **Note**: Ensure that the data format of the WebSocket messages remains consistent. Any change in the message structure could lead to pipeline failures.

## Open Source Setup
Make sure you have `Blink` installed or Docker image pulled.
If not - go to [Installation section](Installation.md)

### Specify your tables schema
Describe your WebSocket message schema in the `service` section for Blink

```yaml
service:
  id: 123
  stream_schema:
    - stream: taxi_rides # this is the name of the stream. You can have only one stream for WebSocket connector
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
Now you can set WebSockets config for source. Follow the example below:

```yaml
source:
  driver: websocket
  config:
    url: wss://databrew-ws-gateway.fly.dev/ws
```

## Important Section

In this section, we highlight crucial considerations and best practices for the WebSocket source connector in the DataBrew project.

- **Single Stream Support**: The WebSocket connector is designed to support only one stream. Ensure that the specified stream provides all the necessary data for your pipeline.
- **Data Format Consistency**: It's imperative that the data format of the messages remains unchanged. Variations in the message structure can disrupt the data integration process and break the pipeline.
- **Error Handling**: Implement robust error handling and monitoring to quickly identify and resolve any issues related to data format inconsistencies or connection problems.

## Conclusion

In this document, we covered the setup and important considerations for using the WebSocket source connector with the DataBrew project. By ensuring a consistent data format and understanding the limitations of single stream support, you can integrate real-time data into your pipeline effectively.

For further assistance or queries, please contact [support](mailto:support@databrew.tech).
