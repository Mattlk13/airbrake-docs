## Step 1: Install the latest version of pybrake

Airbrake for Flask uses our official Python notifier
[pybrake](https://github.com/airbrake/pybrake). To install run:

{% highlight bash %}
pip install pybrake
{% endhighlight %}

## Step 2: Configure the Airbrake Flask middleware

Replace the placeholder `project_id` and `project_key` values from the example
below with the real values from your project's setting page.

{% highlight python %}
from flask import Flask
import pybrake.flask

app = Flask(__name__)
app.config['PYBRAKE'] = dict(
    project_id=123123,
    project_key='FIX-ME',
)
app = pybrake.flask.init_app(app)


@app.route('/')
def hello_airbrake():
    return 'Hello, Airbrake!'
{% endhighlight %}
