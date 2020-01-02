---
layout: classic-docs
title: Installing Airbrake in a Redux application
short-title: Redux
language: redux
categories: [installing-airbrake]
description: Installing Airbrake in a Redux application
---

![](https://s3.amazonaws.com/document-resources/jsbrakeman.png)

{% include_relative airbrake-js/features.md %}


## 1. Add dependencies
``` bash
npm install @airbrake/browser redux-airbrake --save
```

## 2. Import dependency
``` js
import { Notifier } from '@airbrake/browser';
import airbrakeMiddleware from 'redux-airbrake';
```

## 3. Configure & add middleware
``` js
const airbrake = new Notifier({
    projectId: 123,
    projectKey: 'abcdefg12345678'
});

const errorMiddleware = airbrakeMiddleware(airbrake);

export const store = createStore(
    rootReducer,
    applyMiddleware(
        errorMiddleware
    )
);

export default store;
```

The [redux-airbrake middleware](https://github.com/alexcastillo/redux-airbrake)
also supports additional options like
[sending last action & state to Airbrake](https://github.com/alexcastillo/redux-airbrake#sending-last-action-and-store-state-to-airbrake)
and
[Adding extra details to errors before they are sent](https://github.com/alexcastillo/redux-airbrake#adding-notice-annotations-optional).

{% include_relative airbrake-js/going-further.md %}
