

 ### 10. pageSection()
 <hr>
  
 This function retrieves either a section  items based on the provided alias.
  
 ##### Parameters
 - `$alias` : The alias of the section item(s) to retrieve.
 - `$sectionData` (optional)  : An array or collection of section items.


 ##### Return Value
  - The HTML content of the section item(s).
  
 ##### Example Usage
   ```
  
  {! pageSection('our-brands') !}

  //or
  {! pageSection('our-brands', $sectionData) !}
   
   ```

### 10. socialLink()
<hr>

   This function generates HTML code for social media icons based on the configuration stored in the settings.
    
   ##### Return Value
- The HTML code containing links to social media profiles.
   ##### Example Usage
  ```
  {!  socialLink() !}
  
    ```
 
### banners()
<hr>
   This function generates HTML code for banners based on the provided array of banner objects.
    

   ##### Return Value
- The HTML code containing banners.
   ##### Example Usage
  ```
     
     {!  banners() !}
  
    ```
  
## Content Service Functions

### homeContent()
<hr>

The `homeContent()` function retrieves all the home items for the home page content.

##### Return Value

This function returns a collection of `HomeItem` models where the `h_status` field is equal to `1`, sorted by the `h_order` field in ascending order.

##### Example Usage
```
 @foreach(Content::homeContent() as $item)
    {!! $item->h_content !!}
 @endforeach

```

### recentArticles() 
<hr>

The `recentArticles()` function retrieves the specified number of recent published articles with the categories relationship from the database. It uses the Laravel Eloquent ORM to make the database query.

##### Function Parameters 
- `$articleNum` : (optional) - The number of recent articles to retrieve. It defaults to 10 if not specified.

##### Return Value
The function returns a collection of model instances containing the retrieved articles and their associated categories.

##### Example Usage
```
 @foreach(Content::recentArticles(4) as $item)
    ....
 @endforeach

```
<hr>


