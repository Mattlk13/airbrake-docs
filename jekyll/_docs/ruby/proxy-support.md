---
layout: classic-docs
title: Proxy support
categories: [ruby]
last_updated: May 11, 2016
description: Proxy support
---

## Can I configure Airbrake to send errors through a proxy?

Yes, you can! If your server is not able to directly reach the Airbrake
servers you can configure the Airbrake ruby notifier to send errors through
your proxy.

Configuring Airbrake to use your proxy is as simple as setting the relevant proxy
options in the initializer

### Configuring Airbrake V5 to use a proxy

{% highlight ruby %}
Airbrake.configure do |c|
  c.proxy = {
    host: 'example.com'
    port: 8080
    user: 'user'
    password: 'p4ssw0rd'
  }
end
{% endhighlight %}

We have more config options in https://github.com/airbrake/airbrake/wiki
