# NATS Target Connector

## Introduction

This document provides a detailed guide on setting up the NATS target connector for the DataBrew project. The NATS connector facilitates efficient and reliable streaming of processed data into your NATS subjects, ensuring that your data pipeline's output is seamlessly integrated into your messaging system.

## Requirements

Before setting up the NATS target connector, ensure you meet the following requirements:

- Access to your NATS server or NATS.io cloud service.
- Necessary permissions to publish messages to the NATS subjects.
- Understanding of your NATS server's configuration and subject hierarchy.

### Preparing Your NATS Environment

To ensure smooth integration:

- **Subject Configuration**: Ensure that the subjects you intend to publish messages to are properly configured in your NATS server.
- **Security & Access Control**: Verify that the DataBrew project's user account or service has the required permissions to publish messages to the desired subjects.

## Cloud Setup

This section guides you through setting up the NATS target connector in the cloud for the DataBrew project.

### Setting up in Cloud

1. **Access DataBrew Cloud Platform**: Navigate to [DataBrew Cloud App](https://app.databrew.tech).
2. **Create a New Target Connector Instance**: Follow these steps...
    - Step 1: Choose 'NATS' from the list of available target connectors.
    - Step 2: Provide the necessary connection details, including your NATS server URL, authentication details, and target subject.
    - Step 3: Configure additional settings like message serialization format, acknowledgments, and queue group, as required.
    - (Include screenshots or code snippets if necessary)

## Open Source Setup
Make sure you have `Blink` installed or Docker image pulled.
If not - go to [Installation section](Installation.md)

### Specify destinations
Blink configuration should look as follows:
```yaml
sink:
  driver: nats
  config:
    url: ${NATS_URI} # Full uri with auth info  like: nats://user:password@host:port
    subject: subject_name
```

## Important Section

In this section, we include essential tips, tricks, and important information related to the NATS target connector for the DataBrew project.

- **Subject Hierarchy and Naming**: Plan and understand your subject hierarchy and naming conventions to ensure proper message routing and data organization.
- **Monitoring and Reliability**: Implement monitoring on your NATS server to track message delivery, and consider setting up redundancy and high availability for critical data streams.

## Conclusion

In this document, we covered the requirements, cloud setup, and important notes for setting up the NATS target connector for the DataBrew project. By following the steps outlined, you can ensure that your processed data is efficiently and reliably streamed to your NATS subjects.

For further assistance or queries, please contact [support](mailto:support@databrew.tech).
