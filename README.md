Kibana Dashboard for KrakenD
====
This repository contains a Kibana dashboard ready to be used on your Elastic installation. It works both on KrakenD Enterprise and KrakenD Community Edition.

![Kibana screenshot](screenshots/kibana-screenshot.png)

To import the Kibana dashboard included in this repository execute the following command **once your Kibana is up and running**:

```shell
    curl -X POST "localhost:5601/api/saved_objects/_import" -H "kbn-xsrf: true" --form file=@config/elastic/dashboard.ndjson -H "kbn-xsrf: true"
```

Replace `localhost:5601` with your IP and port.

To configure KrakenD to push logs to Kibana, see the [logging documentation](https://www.krakend.io/docs/logging/)

## Contribute!
This is an example dashboard and it can be improved in many ways.

Try it out! If it doesn't help you, or you think you can add additional metrics, please open a pull request!

Thanks!

---

If you have any questions or doubts, you can find our support resources at [https://www.krakend.io/support/](https://www.krakend.io/support/)
