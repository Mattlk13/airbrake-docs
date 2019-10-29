---
layout: classic-docs
title: Structured logging
categories: [features]
description: Sending structured text data
---

To improve Airbrake's grouping and aggregation of errors, it is strongly advised to use a machine readable format in error messages. Airbrake supports 2 main formats:

- JSON appearing anywhere in the error message, for example `User not found {"id":123,"email":"support@airbrake.io"}`.
- `key=value` pairs, for example `User not found id=123 email="support@airbrake.io"`.

In both variants, Airbrake extracts the data from the error message and saves it in the `context.messageParams` field, which can be used later for aggregation.

Error messages like `User 123 with email support@airbrake.io not found` are also parsed, but it is a much less reliable way to send structured data.

In addition to improved grouping and aggregation of errors, this structured
logging enables you to use our powerful advanced features including:

- [Custom search filters](/docs/airbrake-faq/how-do-i-use-search-and-filtering/#filtering-by-custom-attributes)
- [Custom aggregations](/docs/features/custom-aggregations/#custom-aggregations)
