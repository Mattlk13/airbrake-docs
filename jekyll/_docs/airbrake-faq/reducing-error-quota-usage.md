---
layout: classic-docs
title: Reducing error quota usage
categories: [airbrake-faq]
description: Reducing error quota usage
---

If your applications are sending more errors than your plan allows, this can
result in error loss and reduced debugging effectiveness. There are several
options to reduce your error quota usage.

### Ignore noisy errors

Once you have identified a noisy error you can configure your notifier to avoid
reporting it to Airbrake. Please visit your notifier's GitHub repo if you don't
see your language in the examples below.

#### [Ignore errors in Ruby](https://github.com/airbrake/airbrake-ruby#airbrakeadd_filter)

```ruby
Airbrake.add_filter do |notice|
  notice.ignore! if notice.stash[:exception].is_a?(NoisyException)
end
```

#### [Ignore errors in Javascript](https://github.com/airbrake/airbrake-js/tree/master/packages/browser#filtering-errors)

```js
airbrake.addFilter(function(notice) {
  if notice.errors[0].type === "NoisyException" {
    return null;
  }
  return notice;
});
```

#### [Ignore errors in Go](https://github.com/airbrake/gobrake#ignoring-notices)

```go
airbrake.AddFilter(func(notice *gobrake.Notice) *gobrake.Notice {
  if notice.Errors[0].Type == "NoisyException" {
    return nil
  }
  return notice
})
```

#### [Ignore errors in PHP](https://github.com/airbrake/phpbrake/#ignoring-specific-exceptions)

```
$notifier->addFilter(function ($notice) {
  if ($notice['errors'][0]['type'] == 'NoisyException') {
    return null;
  }
  return $notice;
});
```

#### [Ignore errors in .NET](https://github.com/airbrake/sharpbrake#addfilter)

```
airbrake.AddFilter(notice =>
{
  var exception = notice.Exception as HttpException;
  if (exception != null && exception.GetType() == NoisyException)
      return null;

  return notice;
});
```

### Accept only a portion of noisy errors

Once you have identified the noisy errors that are depleting your quota, this
config code will accept only a sample of the occurrences. This example is for
our ruby notifier but you can use this strategy for any notifier that supports
the add_filter configuration option.

```ruby
noisy_errors = [Resque::TermException, NoMethodError, Redis::CannotConnectError]

Airbrake.add_filter do |notice|
  next unless noisy_errors.include?(notice.stash[:exception])

  # Ignore this error 90% of the time.
  notice.ignore! if rand(1..10) <= 9
end
```
