# Digitalbit


| **Laravel** | **DigitalBit** |
|-------------|---------------------|
| 10.0        | 1.0.0                |

`sourcebit/digitalbit` 

## Install

To install through Composer, by run the following steps:


### composer.json


``` json
{
    "repositories": [
          {
              "type": "vcs", or path
              "url": "git_url", or packages path
              "options": {
                  "symlink": true
              }
          }
      ],

    "require": {
        "sourcebit/digitalbit": "dev-main"
    },
    "autoload": {
        "psr-4": {
            "Sourcebit\\Digitalbit\\": "packages/sourcebit/digitalbit/src/"
        },
       
},
```



**Tip: don't forget to run `composer dump-autoload` afterwards.**
**Tip: don't forget to run `composer update` afterwards.**

Optionally, publish the package's configuration file by running:
``` bash
php artisan digitalbit:install
```


### composer.json

``` json
{
   
 "autoload": {
    "files": [
                "app/Helpers/theme_helper.php"
            ]
    },

}
```
**Tip: don't forget to run `composer dump-autoload` afterwards.**

#### Update CSS & JS Files
This command updates the public backend CSS and JS files.
**Files to be updated:**
- css
- fonts
- js
- plugins

To execute the command, run the following code in your terminal:

``` bash
php artisan digitalbit:update
```

#### Database Update
** APP_URL`/author/sql-query` this Url hits .**

#### sql query

``` json
    ALTER TABLE `content` CHANGE `catid` `catid` INT(10) NULL DEFAULT '0';
    ALTER TABLE `content` CHANGE `hits` `hits` INT(10) NULL DEFAULT '0';
    ALTER TABLE `content` CHANGE `attribs` `attribs` VARCHAR(200) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL DEFAULT '0';
    ALTER TABLE `menu` CHANGE `m_showcat` `m_showcat` TEXT CHARACTER SET utf8 COLLATE utf8_general_ci NULL;
    ALTER TABLE `menu` CHANGE `m_attribs` `m_attribs` VARCHAR(300) CHARACTER SET utf8 COLLATE utf8_general_ci NULL;
    ALTER TABLE `category` CHANGE `cat_description` `cat_description` TEXT CHARACTER SET utf8 COLLATE utf8_general_ci NULL;
    ALTER TABLE `category` CHANGE `cat_picture` `cat_picture` VARCHAR(300) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL;

```

#### Table list
1. category
2. category_article
3. content
4. menu
5. menu_type
6. tbl_home
7. tbl_banners
8. tbl_gallery

#### New Theme Crate
``` 
Theme folder structure
. resources/views/frontend/{themeName}
    theme_data this (theme.jpg, theme.json & theme.sql) file crate

theme.json
    {
      "themeName": "EcoThread",
      "themeSlug": "EcoThread",
      "developer": "MD. RASEL",
      "themeKey": "",
      "themeVersion":"03",
      "itemLists":[
        "public","resources"
      ],
      "path":[
        "public","resources"
      ]
    }
. public/frontend/{themeName}
```
