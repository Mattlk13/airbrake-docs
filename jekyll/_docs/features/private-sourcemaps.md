---
layout: classic-docs
title: Private Sourcemaps
short-title: Private Sourcemaps
categories: [features]
description: Private sourcemaps
---

![](https://s3.amazonaws.com/document-resources/jsbrakeman.png)

Private sourcemaps are a core feature available on all paid plans along with
[public sourcemaps](/docs/features/public-sourcemaps/).

This guide assumes you have already [installed Airbrake in your JavaScript
app](/docs/installing-airbrake/installing-airbrake-in-a-javascript-application).

## Benefits of private sourcemap uploads

Uploading private sourcemaps to Airbrake:

- Allows us to de-minify your JavaScript files and present your backtraces with
  meaningful line numbers that look like pre-minified source code
- Provides a more accurate picture of the error and faster debugging times
- Gives you all of the debugging benefits of publicly hosted sourcemaps
  without exposing your source code

## Generating sourcemaps

Generating sourcemaps can be done with
[uglifyjs](https://github.com/mishoo/UglifyJS2#cli-source-map-options) and
[webpack](https://webpack.js.org/configuration/devtool/#production).  Here is an
example to minify and create a sourcemap for an `app.js` file:

```sh
uglifyjs app.js -o app.min.js -c -m \
  --source-map "root='https://example.com/',url='app.min.js.map'"
```

This command will create two new files, a minified `app.min.js` file and a
sourcemap named `app.min.js.map`. The sourcemap file is what we will be
uploading to Airbrake.

## Uploading sourcemaps

Continuing on with our above example, the next steps assume the minified version
of `app.js` is publicly available at `https://example.com/app.min.js`.

The bottom of the `app.min.js` file should have a comment with the name of the
of the sourcemap.

```js
//# sourceMappingURL=app.min.js.map
```

#### Upload your sourcemap

The following curl command assumes that your sourcemap file `app.min.js.map` is
in the current directory and will upload your sourcemap to airbrake.

```sh
curl https://airbrake.io/api/v4/projects/PROJECT_ID/sourcemaps \
  -X POST \
  -H 'Authorization: Bearer PROJECT_API_KEY' \
  -F file=@app.min.js.map \
  -F name="https://example.com/app.min.js.map"
```

Note: `PROJECT_ID` and `PROJECT_API_KEY` will need to be switched out for the real
values from your project.

#### Custom sourcemap URLs

If JavaScript file is not publicly accessible you need to manually
associate the file and the sourcemap by providing a custom sourcemap URL.

Custom sourcemap URLs are supported by assigning a special property of
`notice.context` called `sourceMaps`. The keys of the `sourceMaps` object
represent shell filename patterns and the values are URLs of your sourcemaps.

```js
airbrake.addFilter(function(notice) {
  notice.context.sourceMaps = {
    'https://example.com/app.min.js': 'https://example.com/app.min.js.map'
  };
  return notice;
});
```
Filename pattern uses Unix glob-like syntax:

- `*` matches any sequence of non-path-separators
- `**` matches any sequence of characters, including path separators
- `?` matches any single non-path-separator character

For example:

```js
airbrake.addFilter(function(notice) {
  notice.context.sourceMaps = {
    '**/app.min.js': 'https://example.com/app.min.js.map'
  };
  return notice;
});
```

#### Viewing your uploaded sourcemaps

You can view a list of the sourcemaps that you've uploaded to Airbrake using
this endpoint:

```
https://airbrake.io/api/v4/projects/PROJECT_ID/sourcemaps?key=USER_AUTH_TOKEN
```

You can get your `user auth token` in [your personal settings page](https://airbrake.io/users/edit).

### Troubleshooting

For your private sourcemap upload to function correctly it's important you check that:

- The `name` for the file `https://example.com/app.min.js.map` should be fully
  qualified.
- Your `app.min.js` file has the `sourceMappingURL` comment at the bottom of
  that file, e.g. `//# sourceMappingURL=app.min.js.map`

We also support public sourcemaps please visit our [official airbrake-js repo](https://github.com/airbrake/airbrake-js/tree/master/packages/browser#source-maps) for more info.

#### Sourcemap file size limit

Public and private sourcemaps have a file size limit of 32MB. Sourcemaps greater than 32MB will return a 400

```
{"code":400,"type":"Bad Request","message":"http: request body too large"}

```

### Example of how Airbrake looks for your sourcemaps
- Your project sends an error to Airbrake
- Airbrake processes the error and sees a filename
  `http://localhost:3000/javascript/app.js`
- Airbrake tries to download `http://localhost:3000/javascript/app.js` to
  extract sourcemap location, but it can't since that file is on localhost
- Airbrake then looks at `notice.context["sourceMaps"]` in case you manually
  associated a sourcemap with the `http://localhost:3000/javascript/app.js`
  file
- From the `sourceMaps` value, Airbrake discovers that the sourcemap is located
  at `http://localhost:3000/javascript/maps/app.js.map`, but Airbrake can't
  download it since, again, it's localhost
- Airbrake then finally checks if you manually uploaded that file using this
  **private sourcemap feature**
