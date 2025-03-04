---
title: Установка
---

### Проверьте версию PHP

Flextype невероятно легко настроить и запустить.  
Убедитесь, что у вас есть хотя бы PHP версии 7.2.0+, перейдя в терминал и набрав `php -v`:

      php -v
      PHP 7.2.20 (cli) (built: Jul  5 2019 12:51:26) ( NTS )
      Copyright (c) 1997-2018 The PHP Group
      Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
          with Zend OPcache v7.2.20, Copyright (c) 1999-2018, by Zend Technologies
    

### Использование (S)FTP

[Загрузите последнюю версию.](http://flextype.org/en/downloads)

Распакуйте содержимое в новую папку на локальном компьютере и загрузите на свой веб-узел с помощью выбранного FTP-клиента. Затем, когда файлы загружены, удостоверьтесь в том, что вы выставили права chmod (для *nix систем) `755`, либо `777` на следующие директории:

* `site/`

### Использование Composer

Вы можете легко установить Flextype с помощью Composer.

     composer create-project flextype/flextype
    

Also you may need to install vendor libs for default plugins and default theme. Go to your project folder, and run:

     cd site/plugins/admin
     composer install
     npm install
     gulp
    
     cd ../../../
    
     cd site/plugins/site
     composer install
    
     cd ../../../
    
     cd site/themes/default
     npm install
     gulp
    

### Использование командной строки

Если у вас есть доступ к командной строке, вы можете легко установить Flextype, выполнив несколько команд. Для начала создайте директорию, в которую хотите установить Flextype, если она ещё не создана. Затем перейдите в директорию и выполните следующие команды:

      wget https://github.com/flextype/flextype/releases/download/v0.9.6/flextype-0.9.6.zip
      unzip flextype-0.9.6.zip
      chmod -R 0777 site/
    

### Проблемы при установке

##### Не работают под-страницы

Домашняя страница вашего сайта работает, но не работают под-страницы сайта?

1. Удостоверьтесь, что в папке с установленным Flextype присутствует файл .htaccess.
2. Проверьте, активирован ли на вашем сервере mod_rewrite.
3. Please try setting the RewriteBase in the .htaccess file:
    
    RewriteBase /

Если вы запускаете Flextype в под-папке сайта, установите RewriteBase в соответствии с именем под-папки:

      RewriteBase /my-subfolder/
    

## Установка темы

1. Разархивировать тему в папку `/site/themes/`
2. Перейдите в `/site/config/settings.yaml` и обновите настройку `` с вашим именем темы.
3. Сохранить ваши изменения.

## Установка плагинов

1. Разархивировать плагин в папку `/site/plugins/`