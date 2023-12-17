# Create Source Data Connector

Source data connector is a general Data Connector that will be used to consume the data from your data source

> DataBrew recognises every data source or destination as a streaming connector (even the databases). These connectors
can support either consuming the data or producing it. Some of them can support both, meaning you can stream data changes
from PostgreSQL and store it in on fly.

## Create a new Source Data Connector

Open a cloud DataBrew dashboard [Here](https://app.databrew.tech/connectors)
At the beginning it will have no connectors create but, we can create a new one by pressing `New Connector` button

This will open a connector creation interface and, you will see all the supported connector types we can start with

### Source or target
By the default you will be given two options before selecting the connector type. You can create **source** or **target**
connector. In this part of the manual will start with creating a source, but you can create a destination first. 
Process is actually the same.

Find desired connector engine type and hit it with the mouse. It will open a new window with the connector setup interface

Here you will be asked to enter some credentials to make possible for DataBrew to connect to your data source.

> Each connector is different, but we have a guide prepared for a single one of them. Press `Setup guide` on the right to 
> open the manual 


## Configure **stream** for the Data Connector
In order to support various features like database replication and proper schema mutation on fly - DataBrew needs to know 
what data you are going to send over the pipeline.

That's why we introduce a new term `stream`. You can think about stream as a single table in your database. 

For example your Source Data Connector (e.g. PostgreSQL) may have a few tables you want to process.
DataBrew will recognize each table as individual stream with its own properties (read columns). So you will be able to 
process multiple tables in a single data pipeline but, apply processors only for a few.

This is required for every Source Data Connector you will create. 

## Next step
As soon as we configured Source Data Connector we can move on to the next step and create a Destination Data Connector