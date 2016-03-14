title: Use Coffeescript in a Django app
updated: 2013-07-14 20:00:00
os: [macosx, windows, linux]
tags: [coffeescript, python, django]
deps: [install-coffeescript]
contributors: ["http://www.github.com/sloria"] 
description: Using Coffeescript in Django is much simpler than you might think.

First, set up [django-compressor][]. 

```bash
# Install django-compressor
$ pip install django_compressor
```

Include the following in your `settings.py`.

```python
# settings.py

INSTALLED_APPS = [
    # Other apps...
    'compressor',
]

STATICFILES_FINDERS = (
    'django.contrib.staticfiles.finders.FileSystemFinder',
    'django.contrib.staticfiles.finders.AppDirectoriesFinder',
    # other finders..
    'compressor.finders.CompressorFinder',
)

COMPRESS_PRECOMPILERS = (
    ('text/coffeescript', 'coffee --compile --stdio'),
)
```

That's it! You can now include `.coffee` files in your html. Make sure to include them between `{% compress js %}` tags and set the `type` attribute for the script tag to `text/coffeescript`. 

```html
# some_template.html

{% compress js %}
<script src="{{ STATIC_URL }}coffee/cupofjoe.coffee" type="text/coffeescript"></script> 
{% endcompress %}
```

[django-compressor]: http://django_compressor.readthedocs.org/en/master/
