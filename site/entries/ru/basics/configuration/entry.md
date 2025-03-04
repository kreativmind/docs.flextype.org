---
title: Конфигурация
---
Flextype позволяет конфигурировать сайт любым удобным для вас способом, и это благодаря мощным и гибким опциям конфигурации, которые делают это возможным.

Все файлы конфигурации Flextype написаны в синтаксисе YAML с расширением файла `.yaml`. YAML очень интуитивно понятен, что делает его очень удобным как для чтения, так и для записи.

Вы можете обновить и создать конфигурацию сайта, отредактировав файл.`/site/config/settings.yaml`

    # The title of the website
    title: Flextype
    
    # The description of the website
    description: Build fast, flexible, easier to manage websites with Flextype.
    
    # The keywords of the website
    keywords: flextype, php, cms, flat-file cms, flat cms, flatfile cms, html
    
    # The robots of the website
    robots: index, follow
    
    # The name and email address of the website author
    author:
      email: ''
      name: ''
    
    # Set the timezone to be used on the website.
    # For a list of valid timezone settings, see:
    # http://php.net/manual/en/timezones.php
    timezone: UTC
    
    # Charset
    #
    # Set internal character encoding.
    #
    # Currently the following names are supported:
    # http://php.net/manual/en/function.mb-regex-encoding.php#121645
    charset: UTF-8
    
    # The theme to use.
    #
    # Don't edit the provided theme templates directly, because they get updated
    # in next releases. If you wish to modify a default theme, copy its folder, and
    # change the name here accordingly.
    theme: default
    
    # The locale that'll be used by the Flextype.
    locale: en_US
    
    # Valid date format
    #
    # - date_format: Valid date format
    #
    # - date_display_format: Valid date format to display
    date_format: 'd-m-Y H:i'
    date_display_format: 'd-m-y G:i'
    
    # The entries settings§
    #
    # - main:        Main entry
    # - media.upload_images_quality: Image quality
    # - media.accept_file_types: Define the file types (extensions to be exact) that are acceptable for upload.
    entries:
      main: home
      media:
        upload_images_quality: 70
        upload_images_width: 1600
        upload_images_height: 0
        accept_file_types: gif, jpg, jpeg, png, ico, zip, tgz, txt, md, doc, docx, pdf,
          epub, xls, xlsx, ppt, pptx, mp3, ogg, wav, m4a, mp4, m4v, ogv, wmv, avi, webm,
          svg
      error404:
        title: Error 404
        description: We're sorry but the page you are looking for doesn't appear to exist!
        content: We're sorry but the page you are looking for doesn't appear to exist!
        template: default
    
    # Display errors
    #
    # - display: Display errors or not.
    errors:
      display: false
    
    # Cache
    #
    # - enabled:         Set to true to enable caching
    #
    # - prefix:          Cache prefix string (prevents cache conflicts)
    #
    # - driver:          Available drivers: auto (will get one from installed cache drivers), apcu,
    #                    apc, array, wincache, xcache, memcache, memcached, redis, file.
    #
    # - lifetime:        Lifetime of cached data in seconds
    #
    # - redis.socket:    Path to redis unix socket (e.g. /var/run/redis/redis.sock),
    #                    false = use server and port to connect
    #
    # - redis.password   Redis password
    #
    # - redis.server     Redis server
    #
    # - redis.port       Redis port
    #
    # - memcache.server  Memcache server
    #
    # - memcache.port    Memcache port
    #
    # - memcached.server Memcached server
    #
    # - memcached.port   Memcached port
    #
    # - sqlite3.database SQLite3 Database
    #
    # - sqlite3.table    SQLite3 Table
    cache:
      enabled: true
      prefix: flextype
      driver: auto
      lifetime: 604800
      memcache:
        server: localhost
        port: 11211
      memcached:
        server: localhost
        port: 11211
      redis:
        socket: false
        password: false
        server: localhost
        port: 6379
      sqlite3:
        database: flextype
        table: flextype
    
    # Admin Panel
    #
    # - themes:  Theme (dark, light)
    admin_panel:
      theme: light
    
    # Whoops
    #
    # - editor: emacs, idea, macvim, phpstorm, sublime, textmate, xdebug, vscode, atom, espresso
    #
    # - page_title: page title
    whoops:
      editor: atom
      page_title: Error!
    
    # Slim
    #
    # - display_error_details: When true, additional information about exceptions are
    #                          displayed by the default error handler.
    #
    # - add_content_length_header: When true, Slim will add a Content-Length header to
    #                              the response. If you are using a runtime analytics tool,
    #                              such as New Relic, then this should be disabled.
    #
    # - router_cache_file: Filename for caching the FastRoute routes. Must be set to
    #                      a valid filename within a writeable directory. If the file
    #                      does not exist, then it is created with the correct cache
    #                      information on first run. Set to false to disable the FastRoute
    #                      cache system.
    #
    # - determine_route_before_app_middleware: When true, the route is calculated before
    #                                          any middleware is executed. This means that you
    #                                          can inspect route parameters in middleware if you need to.
    #
    # - output_buffering: If false, then no output buffering is enabled.
    #                     If 'append' or 'prepend', then any echo or print statements
    #                     are captured and are either appended or prepended to the Response
    #                     returned from the route callable.
    #
    # - response_chunk_size: Size of each chunk read from the Response body when sending to the browser.
    #
    # - http_version: The protocol version used by the Response object.
    display_error_details: true
    add_content_length_header: true
    router_cache_file: false
    determine_route_before_app_middleware: false
    output_buffering: append
    response_chunk_size: 4096
    http_version: '1.1'
    
    # Twig
    #
    # - auto_reload: When developing with Twig, it's useful to recompile the template
    #                whenever the source code changes. If you don't provide a value
    #                for the auto_reload option, it will be determined automatically
    #                based on the debug value.
    #
    # - debug:       When set to true, the generated templates have a __toString()
    #                method that you can use to display the generated nodes
    #
    # - charset:     The charset used by the templates.
    #
    # - cache:       Set false to disable caching.
    twig:
      auto_reload: true
      cache: true
      debug: false
      charset: "UTF-8"
    
    # Slugify
    #
    # - separator: By default Slugify will use dashes as separators.
    #              If you want to use a different default separator,
    #              you can set the separator option.
    #
    # - lowercase: By default Slugify will convert the slug to lowercase.
    #              If you want to preserve the case of the string you can set the
    #              lowercase option to false.
    #
    # - trim:      By default Slugify will remove leading and trailing separators before
    #              returning the slug. If you do not want the slug to be trimmed you can
    #              set the trim option to false.
    #
    # - regexp:    You can also change the regular expression that is used to replace
    #              characters with the separator.
    #
    # - lowercase_after_regexp: Lowercasing is done before using the regular expression.
    #                           If you want to keep the lowercasing behavior but your
    #                           regular expression needs to match uppercase letters,
    #                           you can set the lowercase_after_regexp option to true.
    #
    # - strip_tags: Adds in an option to go through strip_tags() in case the string contains HTML etc.
    slugify:
      separator: "-"
      lowercase: true
      trim: true
      regexp: "/[^A-Za-z0-9]+/"
      lowercase_after_regexp: false
      strip_tags: false
    
    # Image
    #
    # - driver: gd or imagick
    image:
      driver: gd


Также вы можете обновить любые настройки сайта в Панели администратора на странице Настройки.
