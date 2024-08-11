## Other Functions 

### text_num( $text, $length) 
 * $text {string} - Full text.
 * $length {integer} - Expected length of the return text.
 * Return: string

Return text from begining to specified length.

```php
  text_num('this is full-text', 2);  // this
``` 

### home() 
 * Return: boolean

return true if it is system root .
  
```php
  // https://domain.com/
  home(); 
  // true;
``` 

### 5. contentUtility()
  <hr>

The `contentUtility` function is a utility function that generates HTML markup for a content utility section. It doesn't accept any parameters.

##### Example Usage
  
   ```
 {! contentUtility()!}
   
   ```
 
### 6. share()
<hr>
  The `share` function is a social share function that generates HTML markup for sharing content on different social media platforms. It takes a `$content` parameter, which is expected to be an object with properties like `title`, `alias`, and `id`.
  
  
  ##### Example Usage
  
   ```
 {! share($content)!}
   
   ```
  <hr>
  
  
### 7. ads()
  <hr>
  The `ads`  function simply echoes the string "No Ads". It can be used as a placeholder for displaying ads in your application.
  
##### Example Usage
   ```
 {{ads()}}
   ```
  <hr>
  
### clean_url( $str, $separator, $lowercase ) 
 * $str {string} - string to clean for the url
 * $separator {string} (Optional) - for word separator. Default value is "-". Other can be "_"
 * $lowercase {boolen} (Optional) - lowercase url or not. Default value is FALSE; 

Return url-friendly string. Bengali suported.

```php
  clean_url('clean url friendly string');  // clean-url-friendly-string 
``` 

### segment($segment, $default, $slash ) 
 * $segment {integer} - segment number of the uri. [1 or 2 or 3]
 * $default {string } (Optional)  - if segment not availabe then return 0 or user define value.
 * $slash {string} (Optional) - if given then return as trailing slash (abc/)

Returns the specified uri segment.

```php
  // http://www.domain.com/abc
  echo segment(1, '', '/'); // abc/
  
``` 