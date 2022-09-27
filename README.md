Telemetry Dashboards for KrakenD
================================
This repository contains **example configurations** to support logging and metrics dashboards:

- Elastic + Logstash + Kibana (ELK) installation.
- Grafana

It also includes two Kibana dashboards, one for the **Access Log** activity and another for the **Application Log** activity.

By using the configurations included here, you will have KrakenD configured for ELK.

![Kibana screenshot](screenshots/kibana-screenshot.png)

## Logstash
The `logstash` folder includes an example of a Logstash configuration. It parses and ingests KrakenD logs for KrakenD Enterprise and KrakenD Community Edition.

To use it, change the **hostname** of your Elasticsearch server and any custom ports you might use. Then, start Logstash with this configuration to properly ingest KrakenD logs.

## Kibana
To import the Kibana dashboard included in this repository, execute the following command **once your Kibana is up and running**. Replace `localhost:5601` if needed:

```shell
curl -X POST "localhost:5601/api/saved_objects/_import" -H "kbn-xsrf: true" --form file=@kibana/dashboard.ndjson -H "kbn-xsrf: true"
```

## KrakenD configuration for ELK
On your `krakend.json`, ensure to include the `telemetry/logging` and `telemetry/gelf` components as shown below. Also, make sure the GELF address is correct.

```json
{
  "$id": "https://www.krakend.io/schema/v3.json",
  "version": 3,
  "extra_config": {
    "telemetry/logging": {
      "level": "DEBUG",
      "@comment": "Prefix should always be inside [] to keep the grok expression working"
      "prefix": "[KRAKEND]",
      "syslog": false,
      "stdout": true
    },
    "telemetry/gelf": {
      "address": "logstash:12201",
      "enable_tcp": false
    }
  }
}
```
## Grafana
The `grafana` folder includes Grafana dashboards that feed from Influx DB. Depending on your Influx version you will need to use a v1 or a v2 (Flux language) dashboard.

The dashboards are published on Grafana Cloud, and you can [import them from there](https://www.krakend.io/docs/telemetry/grafana/), but the source files are in this folder.

## Contribute!
In this repository, you have an example of the ingestion process and dashboard visualization, and you can improve it in many ways.

Try it out! If it doesn't help you, or you think you can add additional metrics or improvements, please open a pull request!

Thanks!

---

If you have any questions or doubts, you can find our support resources at [https://www.krakend.io/support/](https://www.krakend.io/support/)
