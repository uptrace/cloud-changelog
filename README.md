# Uptrace Cloud Changelog

This is a changelog for [Uptrace.dev](https://uptrace.dev/). To get notifications when the changelog
is updated, watch for changes in this repo.

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
