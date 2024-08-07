#Theme Menu

## 1. showMainMenu()
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

## 2. showFooterMenu()
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

## 3. showSideMenu()
<hr>
 - This is used to generate a sidebar menu based on the provided menu data. It accepts two 

 ##### Parameters
 - `$menus`: An array containing the menu items to be displayed.
 - `$dropdown` (optional): A boolean flag indicating whether to display submenus as

 ##### Example Usage
 ```
   // Display the sidebar menu
   {!showSideMenu($menus)!}
   // Display the sidebar menu with dropdown submenus
   {!showSideMenu($menus, true)!}
 ```
 