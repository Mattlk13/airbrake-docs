## Performance Monitoring Beta for Express.js apps

[Airbrake Performance Monitoring](/docs/performance-monitoring/performance-dashboard-features/)
is in **beta** for Express.js projects. To get started, install  our Express.js
middleware as shown in
[our example app](https://github.com/airbrake/airbrake-js/blob/master/packages/node/examples/express/app.js).

**Step 1:** include the Express.js middleware:
```js
const airbrakeExpress = require('@airbrake/node/dist/instrumentation/express');
```

**Step 2:** add the middleware to your app (this middleware should be added
before any routes are defined):
```js
app.use(airbrakeExpress.makeMiddleware(airbrake));
```

Once you deploy your app, you should start seeing performance data
automatically populate in your project's Performance Dashboard.
