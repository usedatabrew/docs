# Configuration

In order to run Blink you have to create a configuration file first.

Configuration file in essential to specify the Data Connectors you want Blink to interact with and the processors 
it has to execute against the data frames

## Configure with file

In this example we will start with the simplest configuration file that will consume data from public WebSocket gateway 
that streams us crypto tokens price changes

For simplification, we will use DataBrew's own public WebSocket Gateway with generated data (they do not reflect real state
of the market) it's developed for testing purposes only

In the configuration file below we specify the following

- We define pipeline id and stream schema in the `service` section
- Define Source Data Connector to consume data from WebSocket gateway
- Apply SQL Filter processor, so we know about BTC price change only
- Add `stdout` Target Data Connector to simply log the data received in our console

```yaml
service:
  id: 123
  pipeline_id: 1234
  stream_schema:
    - stream: crypto_price_change
      columns:
        - name: name
          databrewType: String
          pk: true
          nullable: false
        - name: price
          databrewType: Float64
          pk: false
          nullable: false

source:
  driver: websocket
  config:
    url: wss://databrew-ws-gateway.fly.dev

processors:
  - driver: sql
    config:
      query: "select * from streams.crypto_price_change where name = 'BTC'"

sink:
  driver: stdout
  config: {}
```

## Configure embedded
You can create blink configuration dynamically on fly inside your Golang application, by importing Blink in your app.
Check Blink's [GitHub](https://github.com/usedatabrew/blink) repository for examples to see how you can dynamically add sources, processor and destinations

