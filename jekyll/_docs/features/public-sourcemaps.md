---
layout: classic-docs
title: Public Sourcemaps
short-title: Public Sourcemaps
categories: [features]
description: Public sourcemaps
---

![](https://s3.amazonaws.com/document-resources/jsbrakeman.png)

Public sourcemaps are a core feature available on all paid plans along with
[private sourcemaps](/docs/features/private-sourcemaps).

Using sourcemaps allows you to minify your JavaScript code to increase page
performance while still being able to get relevant backtraces for your app's
errors.

## Using Public Sourcemaps with Airbrake

This guide assumes you have already [installed Airbrake in your JavaScript
app](/docs/installing-airbrake/installing-airbrake-in-a-javascript-application).

In order to enable source map support you have to specify the path to the
source map file according to
[the source map specification](https://sourcemaps.info/spec.html).
For example, `airbrake.min.js` has the following line:

```
//# sourceMappingURL=airbrake.min.map
```

*Please note* that the Airbrake backend downloads the sourcemap file to
process the backtrace. This means that the sourcemap should be publicly
accessible via HTTP. So, for example, don't expect sourcemap support to work
on your local webserver running on `localhost`.

## Sourcemaps and Node.js

For server side sourcemaps, please use the following steps:
1. Upload sourcemap to Airbrake using our [Private Sourcemaps
   feature](/docs/features/private-sourcemaps/)
2. Link the minified JS files to the corresponding sourcemap using the [custom
   sourcemap URLs](/docs/features/private-sourcemaps/#custom-sourcemap-urls)
   feature
