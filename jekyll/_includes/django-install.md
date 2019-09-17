## Step 1: Install the latest version of pybrake

Airbrake for Django uses our official Python notifier
[pybrake](https://github.com/airbrake/pybrake). To install run:

{% highlight bash %}
pip install pybrake
{% endhighlight %}

## Step 2: Configure the Airbrake Django middleware

First you need to add your pybrake config to your Django `settings.py` file
using your project's `id` and `api_key`.

{% highlight python %}
AIRBRAKE = dict(
    project_id=123,
    project_key='FIXME',
)
{% endhighlight %}

The next step is activating the Airbrake middleware.

{% highlight python %}
MIDDLEWARE = [
    ...
    'pybrake.django.AirbrakeMiddleware',
]
{% endhighlight %}

The last step is configuring the airbrake logging handler. After that you are
ready to start reporting errors to Airbrake from your Django app.

{% highlight python %}
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'handlers': {
        'airbrake': {
            'level': 'ERROR',
            'class': 'pybrake.LoggingHandler',
        },
    },
    'loggers': {
        'app': {
            'handlers': ['airbrake'],
            'level': 'ERROR',
            'propagate': True,
        },
    },
}
{% endhighlight %}
