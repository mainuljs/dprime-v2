## Content API
These following Data Api can be used in the home page section.

### $content
* Type: stdClass Object.

Content return the single Article or Post page API Data.

```php
 echo $content->title; // Article or Post Page Title

 echo $content->alias; // Alias of Article or Post

  echo $content->introtext; // Short Text of Article or Post 

  echo $content->fulltexts; // Details of Article or Post

  echo $content->featuredimg; // Features Image Article or Post

  echo $content->hits; // Views of Article or Post

  echo $content->status; // Status Article or Post - active or inactive
 
```
 