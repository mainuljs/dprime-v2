

 

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