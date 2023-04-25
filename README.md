# Uptrace Cloud Changelog

This is a changelog for [Uptrace.dev](https://uptrace.dev/). To get notifications when the changelog
is updated, watch for changes in this repo.

## Apr 25 2023

- Add a separate page to each organization that displays number or ingested bytes, spans, and
  datapoints.

  On that page you can also change **Paddle subscription** that is used to process payments.

  To view org billing info, click Organizations -> Org Name -> Billing and usage.

  ![Org usage](./image/2023-04-25_org-usage.png)

## Apr 19 2023

- Add [AWS CloudWatch intergration](https://uptrace.dev/get/ingest/aws-cloudwatch.html) to collect
  metrics and logs from AWS CloudWatch.

- Add [FluentBit integration](https://uptrace.dev/get/ingest/fluent-bit.html) to ingest logs into
  Uptrace.

## Apr 16 2023

- Histogram metric changed from `per_min($metric_name)` to `per_min(count($metric_name))` for
  clarity. Existing dashboards should be automatically updated.

  You can now also use `per_min` as a general function, for example, `per_min(p50($metric_name))`
  which is the equivalent of `p50($metric_name) / _minutes`.

- Documented [Uptrace Enterprise](https://uptrace.dev/get/enterprise.html) features.

## Apr 5 2023

- Accept errors and spans from [Sentry SDK](https://uptrace.dev/get/ingest/sentry.html). The
  integration was created so you can use
  [Sentry for browsers](https://uptrace.dev/get/ingest/sentry.html#sentry-for-browsers) with
  Uptrace.

## March 20 2023

- Added metrics [pricing](https://uptrace.dev/pricing).

> > The cost of metrics is **$2 for 1000 timeseries**. Uptrace stores 1 datapoint per minute for
> > each timeseries and uses the number of active datapoints to calculate the bill.

> > Also, for every $5 spent on tracing or logs, you get 1000 timeseries for free. For example, if
> > your tracing bill is $100, you get 20k timeseries for free.

> > A timeseries is a metric with an unique set of attributes/labels. For example, if you collect 10
> > metrics on each host and you have 10 hosts, that is 10\*10=100 timeseries.

> > A datapoint is a single measured occurrence of a metric within a timeseries, consisting of a
> > value and timestamp.

## March 18 2023

- Added AlertManager notification channel.

  ![AlertManager](./image/2023-03-22_alertmanager.png)

## March 15 2023

- Allow to customize chart legends. Table and list-based legends are supported.

  ![Chart legend](./image/2023-03-22_chart-legend.png)

## March 9 2023

- Allow to [edit dashboards](https://app.uptrace.dev/metrics/1/7?tab=yaml) using YAML format.

  ![YAML dashboard](./image/2023-03-09_dash-yaml.png)

## March 6 2023

- Allow to customize colors and some chart styles.

  ![Table colors](./image/2023-03-06_table_colors.png)

  ![Chart style](./image/2023-03-06_chart_style.png)

## March 5 2023

- Allow to to name DSN to simplify managing multiple DSNs.

  ![DSN name](./image/2023-03-05_dsn-name.png)

## Feb 24 2023

- Metrics dashboards now support 2 new visualizations types: **tables** and **heatmaps**.

  ![Tables and heatmaps](./image/2023-02-23_heatmap-table.png)

## Feb 16 2023

- Added new notification channel: **webhooks**. Webhooks allow receiving notifications about alerts
  managed by Uptrace via HTTP POST requests.

  ![Webhooks](./image/2023-02-16_webhooks.png)

  For example, you will receive the following JSON message when an alert is created:

  ```json
  {
    "id": "1676471814931265794",
    "eventName": "created",
    "payload": { "custom_key": "custom_value" },
    "createdAt": "2023-02-15T14:36:54.931265914Z",

    "alert": {
      "id": "123",
      "url": "https://app.uptrace.dev/alerting/1/alerts/123",
      "name": "Test message",
      "type": "metric",
      "state": "open",
      "createdAt": "2023-02-15T14:36:54.931265914Z"
    }
  }
  ```

## Feb 15 2023

- Allow to create "Text gauges" at the top of dashboards.

- Allow to quickly change grouping in the Table dashboards. Pinned attributes are displayed first.

  ![Metric facets](./image/2023-02-15_text-gauges.png)

## Feb 10 2023

- Improved `uptrace.tracing.spans` and `uptrace.tracing.events` to fetch data directly from the
  spans table. That means that you can now group and filter by all available span attributes.

- Improved metrics UI to provide attribute facets just like with spans.

  ![Metric facets](./image/2023-02-10_metric-facets.png)

## Feb 08 2023

- Added a view to visualize spans query results as a chart. You can save the resulting view using
  "Saved views" feature.

  ![Spans query results](./image/2023-02-08_spans-timeseries.png)

## Feb 01 2023

- Added an ability to create errors monitors in addition to metrics monitors. Using errors monitors,
  you can include/exclude certain errors by span attributes, for example, to receive notifications
  only for certain environments or services.

  ![Monitor errors](./image/2023-02-01_monitor-errors.png)

## Jan 27 2023

- You can now configure per-project sampling to sample a fraction of spans and drop the rest.

  You can also adjust sampling fraction depending on span attributes, for example, you can have
  different sampling fraction depending on `deployment.environment` attribute.

  Visit the [Billing](https://app.uptrace.dev/billing) page to learn more.

- You can now monitor number of sampled and dropped bytes to get notified when you receive more data
  than usually.

  ![Monitor number of bytes](./image/2023-01-27_monitor-bytes.png)

## Jan 2 2023

- To ease navigation, all alerting-related pages are grouped under the "Alerts" tab.

- You can now configure multiple Slack and PagerDuty notification channels. Channels are associated
  with projects, not users.

- You can specify notification channels immediately when creating metrics monitors.

- Span groups are no longer automatically monitored. Instead, Uptrace converts spans to metrics and
  you can monitor spans metrics using monitors.

  By default, the following metrics are available: `uptrace.tracing.spans`,
  `uptrace.tracing.events`, `uptrace.billing.bytes`. In future, you will be able to create custom
  metrics from spans.

  Using `uptrace.tracing.spans` metric, you can monitor number of spans, errors, error rate, and
  p50/p75/p90/p99 duration.

- You can quickly create metrics monitors from span systems:

  ![System monitor](./image/2023-01-02_system-monitor.png)

  From services and hostnames:

  ![Service monitor](./image/2023-01-02_service-monitor.png)

  And metrics:

  ![Metric monitor](./image/2023-01-02_metric-monitor.png)

## Dec 27 2022

- Improve logs and errors grouping.

## Dec 16 2022

- Allow to filter span facets by attribute key.

## Dec 15 2022

- Added ability to save and restore views:

![Saved views](./image/2022-12-15_saved-views.png)

## Dec 05 2022

- Added ability to pin attributes/facets to the top:

![Pinned facets](./image/2022-12-05_pinned-facets.png)

## Nov 25 2022

- Added ability to retry payments on the billing page.
- You can now change payment details in Paddle without recreating a subscription.

## Nov 15 2022

[Pricing](https://uptrace.dev/pricing/) is updated with the following changes:

- Added more volume-based discounts.

- Removed minimum **$30** payment. If your monthly usage is 70 gigabytes, you will be billed $7
  instead of $30.

- Uptrace now bills for the amount of ingested gigabytes monthly or **every $100**, whichever
  happens first. All payments with receipts are available on your billing page.

- Tail-based sampling is now billed separately at **$0.02** per gigabyte.

- You can disable tail-based sampling to get a discount, but Uptrace will stop processing new spans
  when your monthly budget is fully spent. In that case, you need to increase the budget or wait
  until the next billing cycle.

  When tail-based sampling is enabled, Uptrace makes sure your budget is spent uniformly across the
  month so you always have fresh statistics.

  Tail-based sampling is disabled by default.

- Starting from December 1st, users on the free tier won't be able to use tail-based sampling.

## Nov 1 2022

- Added quick filters by `deployment.environment` and `service.name` attributes.

- Added faceted filters for spans and events.

- Added a project setting to group spans by `deployment.environment` attribute.

- Added a project setting to group spans with `funcs` system by `service.name` attribute.

![Project settings](./image/2022-11-01_project-settings.png)

## Oct 20 2022

- Released an initial version of [uptrace-php](https://github.com/uptrace/uptrace-php)
