---
title: Настраиваемые параметры темы
---

При проектировании темы Flextype дает доступ ко всем видам объектов и переменных из ваших шаблонов Twig. Шаблон Twig предоставляет мощные способы для чтения и манипулирования этими объектами и переменными.

### Основные объекты

Существует несколько основных объектов ****, которые доступны для шаблона Twig, и каждый объект имеет набор переменных **** и **функций**.

#### реестр

Реестр хранит все настройки flextype, тем и плагинов.<br /> Вы можете получить доступ к реестру Flextype через объект реестра.

Применение:

```
{{ registry.settings.theme }} {# returns the currently configured theme #}
```

#### записи

Поскольку Flextype построен с использованием структуры, определенной в папке `/site/entries/`, каждая запись представлена объектом записи.

Объект записи, вероятно, самый важный объект, с которым вы будете работать, так как он содержит всю информацию о текущей странице, на которой вы находитесь в данный момент.

Применение:

```
{{ entry.title }} {# returns the current entry title #}
```

#### entries

Получить одну запись

Применение:

```
{% set about_entry = entries.fetch('about') %}
```

Получить коллекцию записей

Применение:

```
{% set posts = entries.fetch('blog', {}) %}
or
{% set posts = entries.fetchCollection('blog') %}
```

#### assets

Добавить активы в коллекцию

Применение:

```
{% set site = base_url() ~ '/site/themes/' ~ registry.settings.theme ~ '/assets/dist/site/site.min.css' %}
{% do assets.add('css', site, 'site', 1) %}
```

Получить активы из коллекции

Применение:

```
{% for assets_site in assets.get('css', 'site') %}
    {% for assets_by_priorities in assets_site %}
        <link href="{{ assets_by_priorities.asset }}" rel="stylesheet">
    {% endfor %}
{% endfor %}
```

#### emitter

Происходящие события

Применение:
```
{% do emitter.emit('onThemeHeader') %}
```

Выпуск событий партиями

Применение:

```
{% do emitter.emitBatch({'onThemeHeader', 'onSomeOtherEvent'}) %}
```

#### snippets

Execute snippet

Применение:

```
{{ snippets.exec('google-analytics')|raw }}
```

### Глобальные переменные

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
