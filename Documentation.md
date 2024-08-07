# Frontend Documentation
## Helper Functions

### 1. showMainMenu()
<hr>
- This function generates a menu based on a menu array and customizable attributes.


##### Parameters
- `$menu` : An array of menu items.
- `$attributes` :  (optional): An associative array of customizable attributes. The following keys can be set in this array:
    - `navAttr` :Attributes to be added to the top-level `ul` element of the menu.
    - `itemAttr` :Attributes to be added to each menu item `ul li` element.
    - `subNavAttr` :Attributes to be added to the `ul li ul` element of the sub-menu.
    - `itemLinkAttr` : Attributes to be added to each menu item link `ul li a` element.
    - `dropDownAttr` : Attributes to be added to each drop-down menu item `(drop-down) ul li` element.
    - `dropDownLinkAttr` : Attributes to be added to each drop-down menu item link `(drop-down) ul li a` element.
    - `activeItemAttr`: Attributes to be added to the currently active menu item `active li` element.
    - `dropDownLi` : Attributes to be added to each drop-down menu item `ul li ul li` element.
    - `dropDownLiA` : Attributes to be added to each drop-down menu item `ul li ul li a` element.


##### Example Usage
```
    // Customize menu attributes 
    attributes array default class name
    
    @php 
    $attributes = [
        'navAttr'           => 'class="navbar-nav ml-auto"',
        'subNavAttr'        => 'class="dropdown-menu animate__animated animate__fadeIn animate__faster"',
        'itemAttr'          => 'class="nav-item"',
        'itemLinkAttr'      => 'class="nav-link"',
        'dropDownAttr'      => 'class="nav-item dropdown"',
        'dropDownLinkAttr'  => 'class="nav-link dropdown-toggle"',
        'activeItemAttr'    => 'class="nav-item active"',
    ];
    @endphp 
    
    // Generate the menu
    {!showMainMenu($menu, $attributes)!};

```
### 2. showFooterMenu()
<hr>
- The `showFooterMenu` function is used to generate a footer menu based on the provided menu data. It accepts several parameters:

##### Parameters
- `$menus` : An array containing the menu items to be displayed.
- `$attributes` (optional): An array of additional attributes to customize the menu's HTML elements. It can include the following keys:
    - `navUl` : The class attribute for the `<ul>` element of the menu.
    - `navUlLi` : The class attribute for the `<li>` elements of the menu.
    - `navUlLiA` : The class attribute for the `<a>` elements of the menu.
- `$alias` (optional): The alias of the menu type to be displayed as the footer menu.

##### Example Usage
```
    // Display the footer menu with default attributes
    {!showFooterMenu($menus)!}

   // Display the footer menu with custom attributes

   $customAttributes = [
       'navUl'      => 'my-footer-menu',
       'navUlLi'    => 'my-footer-menu-item',
       'navUlLiA'   => 'my-footer-menu-link',
   ];

   {!showFooterMenu($menus, $customAttributes)!}

  // Display the footer menu with default alise `footer-menu` custom alise
 {!showFooterMenu($menus, $customAttributes, 'footer-menu-link')!}

```


### 3. showSideMenu()
<hr>
 The `showSideMenu` function is used to generate a sidebar menu based on the provided menu data. It accepts two parameters:
 - `$menus`: An array containing the menu items to be displayed.
 - `$dropdown` (optional): A boolean flag indicating whether to display submenus as
 
 ##### Example Usage
 ```
   // Display the sidebar menu
   {!showSideMenu($menus)!}
   
   // Display the sidebar menu with dropdown submenus

   {!showSideMenu($menus, true)!}
 
 ```
 
 
 ### 4. viewImage()
 <hr>
 
 The `viewImage` function is used to generate HTML markup for displaying images based on the provided image paths. It accepts two parameters:
 
 - `$imagePaths`: The path or paths of the images to be displayed. If multiple paths are provided, they should be separated by the pipe character (|).
 - `$attributes` (optional): An array of additional attributes to customize the image display.
 
##### Example Usage

```
   $attributes = [
       'withTag' => true,
       'single' => true,
       'title' => 'Image Title',
       'class' => 'img-thumbnail',
       'width' => '300',
       'height' => '200'
   ];

// Display a single image with <img> tag
 {! viewImage($imagePath, $attributes)!}

  // Display a single image path without <img> tag
  $attributes['withTag'] = false;
{! viewImage($imagePath, $attributes)!}

// Display multiple images with <img> tags
$attributes['single'] = false;
{!viewImage($imagePath, $attributes)!}
  
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
  

    
  ### 8. getTheme()
  <hr>
  The `getTheme` function the theme value from the request parameters and sets it in the session. If the theme value is not provided or does not match any existing theme, it falls back to the default theme specified in the configuration.
  
  
  ##### Example Usage
  
   ```
 getTheme()
   
   ```
  <hr>
  
  

### 9. home()
<hr>
 if the current page is the homepage, then the function returns `true` otherwise, it returns `false`
 <hr>
 
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


