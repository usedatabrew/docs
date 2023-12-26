# Metrics

Metrics are one of the most crucial parts of any application. But it's even more important for data pipelines.
DataBrew provides you two ways to export your metrics

- InfluxDB
- Prometheus

Both of these drivers support the same params, so the choice is yours which one to use.

By default, Blink starts local prometheus exporter, so you can find your metrics by setting sup prometheus to scrap them
from `http://localhost:3333/metrics`

If you are interested in exporting your metrics to InfluxDB, you have to adjust a config file as in an example below.
And add `enable_influx: true` and `influx` sections to the `service`:

```yaml
service:
  # the rest of the config for service section goes here
  enable_influx: true
  influx:
    host: # influx host
    token: # token
    org: # string name of the org like: DataBrew, Inc.
    bucket: # name of the bucket 
    group_name: # the group your pipelines related to
    pipeline_id: # the id of the pipeline
```

> Important to know that DataBrew doesn't support an old Influx auth mechanism using username and password