# Overview

DataBrew is a cloud solution that enables developers to create event-driven architecture in days instead of weeks.
Utilizing power of Golang and sophisticated software - we deliver the most cost-efficient and performance-oriented services
So you can build your data pipeline without having a hole in your pocket 😊

## Core concept

TODO::

## Glossary

A definition list or a glossary:

Streaming connectors
: DataBrew recognises every data source or destination as a streaming connector (even the databases). These connectors 
can support either consuming the data or producing it. Some of them can support both, meaning you can stream data changes
from PostgreSQL and store it in on fly.

Processors
: These are one of the main building blocks of the data pipelines. Since your data is treated as a stream - you are allowed
to interact with it on fly. Processors are applied for each record in the data stream independently and allow you to modify 
the data package, drop it from the stream, filter, check with AI or even send it to third-party system.

Pipelines
: Pipelines in DataBrew's terminology are combinations of the Streaming Connectors and Processors. Your data stream may have a
single data source which is passed through a few different processors sequentially and then stored/streamed to the destination
This is the pipeline.


## Next step

Now lets try to create your first data pipeline with DataBrew. It's simple. Let us guide you
