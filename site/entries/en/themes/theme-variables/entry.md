---
title: Theme Variables
---

When you are designing a theme, Flextype gives you access to all sorts of objects and variables from within your Twig templates. The Twig templating framework provides powerful ways to read and manipulate these objects and variables.

### Core Objects

There are several **core objects** that are available to a Twig template, and each object has a set of **variables** and **functions**.

#### registry

Registry stored all flextype, themes and plugins settings.<br>
You can access Flextype registry via the registry object.

Usage:

```
{{ registry.settings.theme }} {# returns the currently configured theme #}
```

#### entry

Because Flextype is built using the structure defined in the `/site/entries/` folder, each entry is represented by a entry object.

The entry object is probably the most important object you will work with as it contains all the information about the current page you are currently on.

Usage:

```
{{ entry.title }} {# returns the current entry title #}
```

#### entries

Fetch single entry

Usage:

```
{% set about_entry = entries.fetch('about') %}
```

Fetch collection of entries

Usage:

```
{% set posts = entries.fetch('blog', {}) %}
or
{% set posts = entries.fetchCollection('blog') %}
```

#### assets

Add asset to the collection

Usage:

```
{% set site = base_url() ~ '/site/themes/' ~ registry.settings.theme ~ '/assets/dist/site/site.min.css' %}
{% do assets.add('css', site, 'site', 1) %}
```

Get assets from the collection

Usage:

```
{% for assets_site in assets.get('css', 'site') %}
    {% for assets_by_priorities in assets_site %}
        <link href="{{ assets_by_priorities.asset }}" rel="stylesheet">
    {% endfor %}
{% endfor %}
```

#### emitter

Emitting events

Usage:
```
{% do emitter.emit('onThemeHeader') %}
```

Emitting events in batches

Usage:

```
{% do emitter.emitBatch({'onThemeHeader', 'onSomeOtherEvent'}) %}
```

#### snippets

Execute snippet

Usage:

```
{{ snippets.exec('google-analytics')|raw }}
```

### Global Variables

```
{{ PATH_SITE }} {# Returns the path to the site directory (without trailing slash). #}
{{ PATH_PLUGINS }} {# Returns the plugins to the root directory (without trailing slash). #}
{{ PATH_THEMES }} {# Returns the path to the themes directory (without trailing slash). #}
{{ PATH_ENTRIES }} {# Returns the path to the entries directory (without trailing slash). #}
{{ PATH_SNIPPETS }} {# Returns the path to the snippets directory (without trailing slash). #}
{{ PATH_FIELDSETS }} {# Returns the path to the fieldsets directory (without trailing slash). #}
{{ PATH_CONFIG_DEFAULT }} {# Returns the path to the default config directory (without trailing slash). #}
{{ PATH_CONFIG_SITE }} {# Returns the path to the site config directory (without trailing slash). #}
{{ PATH_CACHE }} {# Returns the path to the cache directory (without trailing slash). #}
{{ FLEXTYPE_VERSION }} {# Returns the Flextype version #}
{{ PHP_VERSION }} {# Returns the php version #}
```
