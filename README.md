# MODx Revolution

## Установка

* создать на тестовом сервере папку с кодовым названием проекта. Например, dnp.
* с таким же названием, только с префиксом **test_** создать БД (например, *test_dnp*)
* создать юзера БД
 * логин как название проекта с префиксом **u_** (например, *u_dnp*)
 * пароль **<название проекта>** + **kortec**, но заменить **i** на **1**, а **o** на **0** (например, *dnpk0rtec*)
* назначить юзера на БД

При установке администратор по-умолчанию см. в SkyDrive.

## Первичная настройка

* Установить расширения:
 * getResources
* getPage
* wayfinder
* TinyMCE
* Ace
* + те, котороые нужны для текущего проекта
* Изменить настройки системы:
    * в core
        * *manager_date_format* - **d.m.Y**
        * *manager_time_format* - **H:i**
        * *manager_week_start* - **1**
        * *site_name* - **<Название проекта>**
    * в tinymce
        * в *tiny.theme_advanced_blockformats* убрать **h1** (если заголовки 1-го уровня выводятся в шаблоне)
        * *tiny.custom_buttons3* - **tablecontrols**
        * *tiny.custom_plugins* - добавить плагин **table**
* Создать источники файлов
    * **Изображения** - на папку **assets/images**
    * **Файлы** - на папку **assets/files**

## Настройка дружественных URL

1. Создать в корне сайта файл **web.config** с кодом

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="ModX IIS7 Rule 1 (By Simon Fraser)" stopProcessing="true">
                    <match url=".*" ignoreCase="false" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{HTTP_USER_AGENT}" pattern="^.*internal\ dummy\ connection.*$" />
                    </conditions>
                    <action type="CustomResponse" statusCode="403" statusReason="Forbidden" statusDescription="Forbidden" />
                </rule>
                <rule name="ModX IIS7 Rule 2 (By Simon Fraser)" stopProcessing="true">
                    <match url="^(connectors|core|manager|assets)" ignoreCase="false" />
                    <action type="None" />
                </rule>
                <rule name="ModX IIS7 Rule 3 (By Simon Fraser)" stopProcessing="true">
                    <match url="^(.*)$" ignoreCase="false" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" pattern="" ignoreCase="false" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" pattern="" ignoreCase="false" />
                    </conditions>
                    <action type="Rewrite" url="index.php?q={R:1}" appendQueryString="true" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```

2. Установить пакет **Translit** (для автоматической генерации псевдонимов из заголовков)
3. Изменить настройки сайта:
    * *automatic_alias* - **ДА** (Автоматически генирировать псевдоним)
    * *use_alias_path* - **ДА** (Использовать вложенные URL)
    * *friendly_urls* - **ДА** (Использовать дружественные URL)
    * *friendly_alias_translit* - **russian** (Транслитерация псевдонимов)
4. Стереть префикс **html** (Система -> Типы содержимого -> HTML)
5. Пересохранить имеющиеся ресурсы с генерацией новых псевдонимов, заодно убедиться что всё работает

## Карта сайта

### Карта для людей

Создать ресурс с заголовком **Карта сайта** и псевдонимом **sitemap**.
* Шаблон выбрать как у рядовой страницы.
* Отключить html-редактор кода на этом ресурсе.
* Убрать видимость в меню и доступность для поиска.
* В содержимое ресурса вставить:

```html
[[!Wayfinder? &startId=`0` &level=`3` ]]
```

### Карта для роботов

1. Установить пакет GoogleSiteMap.
2. Создать ресурс с заголовком **Sitemap**.
    * Установить шаблон **0 (нет шаблона)**.
    * Выбрать в качестве типа содержимого XML.
    * Отключить html-редактор кода на этом ресурсе.
    * Убрать видимость в меню и доступность для поиска.
    * В содержимом ресурса вставить:

```
[[!GoogleSiteMap? &maxDepth=`3` &showHidden=`1` ]]
```