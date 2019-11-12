---
layout: classic-docs
title: Updating from older Python notifiers
short-title: Updating from older Python notifiers
categories: [performance-monitoring]
description: How to update your Python notifier to the recommended library
---

Get the most out of Airbrake's features and stay up to date with the latest
improvements by updating your project to the latest version of our Python error
reporting library for Django and Flask.

If you are using Python 3.4+, **we would recommend upgrading the Airbrake
library you use from
[`airbrake-python`](https://github.com/airbrake/airbrake-python) to our new
official notifier: [`pybrake`](https://github.com/airbrake/pybrake).**

### Step 1: uninstall `airbrake-python`

```shell
pip uninstall airbrake
```

### Step 2: remove references to the old notifier

Remove references to `airbrake` like imports:

```python
import airbrake

logger = airbrake.getLogger(api_key=*****, project_id=123
```

### Step 3: install new notifier

```shell
pip install -U pybrake
```

#### Configuration

To configure pybrake you will need your Airbrake project's `id` and `api_key`,
these are available from your project's settings page.

```python
import pybrake

notifier = pybrake.Notifier(project_id=123,
                            project_key='FIXME',
                            environment='production')
```

#### Sending errors to Airbrake

```python
try:
    raise ValueError('hello')
except Exception as err:
    notifier.notify(err)
```
