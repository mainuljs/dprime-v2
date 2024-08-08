## Common API Data.

### $appName
 * Type: Property.
 
Name of the Application.
 
```php  
   {{ $appName}}; // VisualCMS  
```


### $appTitle
 * Type: Property.
 
Title of the Application or page title from an specific page.
 
```php  
   {{$appTitle}}; // VisualCMS for Publisher
```


### $title
 * Type: Property.
 
Page title for an specific page.
 
```php  
   {{$title}}; // VisualCMS for Publisher
```

### $appAddress
 * Type: Property.
 
Provide address details defined in the admin settins section
 
```php  
   {{$appAddress}}; 
```

### $contact
 * Type: Property.
 
Provide contact number defined in the admin settins section
 
```php  
   {{$contact}}; 
```

### $logo
 * Type: Property.
 
Get logo of the application.
 
```php  
   {{$logo}}; 
```

### $description
 * Type: Property.
 
Description of the Application or page description from an specific page.
 
```php  
   {{$description}};
```

### $date_format
 * Type: Property.
 
Get logo of the application.
 
```php  
   {{$date_format}}; 
```

### $content_type
 * Type: Property.
 
 Post content type. Generally two types. Single and Multiple
 
```php
  if($content_type === 'single')
  echo $content->title;  
```

### $c_symbol & $c_order
 * Type: Property.
 
Get logo of the application.
 
```php  
   {{$c_symbol}}; 
```
 

