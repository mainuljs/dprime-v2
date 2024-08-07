
## viewImage()
<hr>

The `viewImage` function is used to generate HTML markup for displaying images based on the provided image paths. It accepts two parameters:
 
##### Params
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

## imageGallery()
<hr>
Display all Image of an album Gallery Layouts. (Theme Function)
 
 ##### Params
 - `$galleryObjectData`: Gallery Object Data.
 
##### Example Usage
```
{! imageGallery($galleryObjectData) !}
  
```

## galleryAlbum()
<hr>
Display All Image Album. (Theme Function)
 
##### Params
 - `$galleryNum`: (optional) Gallery Object Data.
 
##### Example Usage
```
{! galleryAlbum($galleryNum) !}
  
```
## videosGallery()
<hr>
 
Display All Videos of an Album. (Theme Function)
 
##### Params
 - `$galleryObjectData`: Video Gallery Object Data.
 
##### Example Usage
```
{! videosGallery($galleryObjectData) !}
  
```