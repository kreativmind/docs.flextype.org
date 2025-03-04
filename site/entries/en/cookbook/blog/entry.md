---
title: Blog
---

A simple blog setup with Flextype.

Structure:
```
site
└── fieldsets
    ├── blog.yaml  
    └── blog-post.yaml  
└── themes
    └── default
        └── templates
            ├── blog.html  
            └── blog-post.html  
└── entries
    └── blog
        ├── entry.md  
        └── hello-world
            └── entry.md
```

<br>

## Create blog fieldset
`/site/fieldsets/blog.yaml`

```yaml
title: Blog
default_field: title
hide: false
sections:
  main:
    title: Main
    fields:
      title:
        title: admin_title
        type: text
        size: 12
      entries_limit:
        title: admin_entries_limit
        type: text
        size: 4/12
  seo:
    title: Seo
    fields:
      description:
        title: admin_description
        type: textarea
        size: 4/12
  settings:
    title: admin_settings
    fields:
      general_heading:
        title: admin_general
        type: heading
      description:
        title: admin_description
        type: textarea
        size: 12
        default: test!
      template:
        title: admin_template
        type: template_select
        size: 4/12
      visibility:
        title: admin_visibility
        type: visibility_select
        size: 4/12
      published_at:
        title: admin_published_at
        type: datetimepicker
        size: 4/12
      routable:
        title: admin_routable
        type: routable_select
        size: 4/12
      menu_heading:
        title: admin_menu
        type: heading
      menu_item_title:
        title: admin_menu_item_title
        type: text
        size: 4/12
      menu_item_url:
        title: admin_menu_item_url
        type: text
        size: 4/12
      menu_item_target:
        title: admin_menu_item_target
        type: select
        options: { _self: _self, _blank: _blank, _parent: _parent, _top: _top }
        size: 4/12
      menu_item_order:
        title: admin_menu_item_order
        type: text
        size: 4/12
```

<br>

### Blog entry
`/site/entries/blog/entry.md`

<img src="[base_url]/image/en/cookbook/blog/create-blog.png?q=70" />

<br>

## Create blog post fieldset
`/site/fieldsets/blog-post.yaml`

```yaml
title: Blog Post
default_field: title
hide: false
sections:
  main:
    title: Main
    fields:
      title:
        title: admin_title
        type: text
        size: 12
      summary:
        title: admin_summary
        type: html
        size: 12
      content:
        title: admin_content
        type: html
        size: 12
      tag:
        title: admin_tags
        type: tags
        size: 8/12
  seo:
    title: Seo
    fields:
      description:
        title: admin_description
        type: textarea
        size: 4/12
  settings:
    title: admin_settings
    fields:
      general_heading:
        title: admin_general
        type: heading
      description:
        title: admin_description
        type: textarea
        size: 12
        default: test!
      template:
        title: admin_template
        type: template_select
        size: 4/12
      visibility:
        title: admin_visibility
        type: visibility_select
        size: 4/12
      published_at:
        title: admin_published_at
        type: datetimepicker
        size: 4/12
      routable:
        title: admin_routable
        type: routable_select
        size: 4/12
      menu_heading:
        title: admin_menu
        type: heading
      menu_item_title:
        title: admin_menu_item_title
        type: text
        size: 4/12
      menu_item_url:
        title: admin_menu_item_url
        type: text
        size: 4/12
      menu_item_target:
        title: admin_menu_item_target
        type: select
        options: { _self: _self, _blank: _blank, _parent: _parent, _top: _top }
        size: 4/12
      menu_item_order:
        title: admin_menu_item_order
        type: text
        size: 4/12
```

<br>

### Blog post entry
`/site/entries/blog/hello-world/entry.md`

<img src="[base_url]/image/en/cookbook/blog/create-blog-post.png?q=70" />

<br>

## Create blog template
`/site/themes/default/blog.html`

```twig
{% extends "themes/default/templates/partials/base.html" %}

{% block content %}
    <h1 class="text-center">{{ entry.title }}</h1>

    {# pagination #}

    {% set page = query.page %}
    {% set tag = query.tag %}

    {% set entries_limit = entries.fetch('blog').entries_limit %}

    {% if tag %}
        {# @todo get count from cache! #}
        {% set entries_length = entries.fetch('blog', {
                                                            'where': {
                                                                'key': 'tag',
                                                                'expr': 'contains',
                                                                'value': tag
                                                            },
                                                            'and_where': [{
                                                                'key': 'visibility',
                                                                'expr': 'nin',
                                                                'value': ['draft', 'hidden']
                                                            }]
                                                        })|length %}

        {% set entries_pages = (entries_length/entries_limit)|round(0, 'ceil') %}
        {% if page < 1 %}
            {% set page = 1 %}
        {% elseif page > entries_pages %}
            {% set page = entries_pages %}
        {% endif %}
        {% set entries_offset = (page-1)*entries_limit %}
        {% if entries_offset < 0 %}{% set entries_offset = 0 %}{% endif %}

        {% set entries = entries.fetch('blog', {
                                                    'where': {
                                                        'key': 'tag',
                                                        'expr': 'contains',
                                                        'value': tag
                                                    },
                                                    'and_where': [{
                                                        'key': 'visibility',
                                                        'expr': 'nin',
                                                        'value': ['draft', 'hidden']
                                                    }],
                                                    'order_by': {
                                                        'field': 'published_at',
                                                        'direction': 'desc'
                                                    },
                                                    'set_max_result': entries_limit,
                                                    'set_first_result': entries_offset
                                                }) %}
    {% else %}

        {# @todo get count from cache! #}
        {% set entries_length = entries.fetch('blog', {
                                                            'where': {
                                                                'key': 'visibility',
                                                                'expr': 'nin',
                                                                'value': ['draft', 'hidden']
                                                            }
                                                        })|length %}

        {% set entries_pages = (entries_length/entries_limit)|round(0, 'ceil') %}

        {% if page < 1 %}
            {% set page = 1 %}
        {% elseif page > entries_pages %}
            {% set page = entries_pages %}
        {% endif %}

        {% set entries_offset = (page-1)*entries_limit %}
        {% if entries_offset < 0 %}{% set entries_offset = 0 %}{% endif %}

        {% set entries = entries.fetch('blog', {
                                                    'where': {
                                                        'key': 'visibility',
                                                        'expr': 'nin',
                                                        'value': ['draft', 'hidden']
                                                    },
                                                    'order_by': {
                                                        'field': 'published_at',
                                                        'direction': 'desc'
                                                    },
                                                    'set_max_result': entries_limit,
                                                    'set_first_result': entries_offset}) %}
    {% endif %}

    {# /pagination #}

    {% for entry in entries %}
        <a href="{{ entry.slug }}" class="blog-post">
            <h3>{{ entry.title }}</h3>
            <p>{{ entry.summary|shortcode|raw}}</p>
            <div>{{ entry.published_at|date(registry.settings.date_display_format) }}</div>
        </a>
    {% endfor %}

    {# pagination navigation #}
    <div class="text-center">
        {% if (page - 1) > 0 %}
            <a href="?page={{ page - 1 }}{% if tag %}&tag={{ tag }}{% endif %}">&larr;</a>
        {% endif %}
        {% if entries_pages is not null and entries_pages != 0 %}
            {{ page }} / {{ entries_pages }}
        {% endif %}
        {% if (page) < entries_pages %}
            <a href="?page={{ page + 1 }}{% if tag %}&tag={{ tag }}{% endif %}">&rarr;</a>
        {% endif %}
    </div>
    {# /pagination navigation #}
{% endblock %}
```

<br>

## Create blog post template
`/site/themes/default/blog-post.html`

```twig
{% extends "themes/default/templates/partials/base.html" %}

{% block content %}
    <h1 class="text-center">{{ entry.title }}</h1>
    <div class="blog-post">
        {{ entry.content|shortcode|raw}}
    </div>
{% endblock %}
```
