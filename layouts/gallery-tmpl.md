## Gallery and Album layouts

<hr>

### Image Gallery

```php

/* * * *
 * Return gallery image html
 * @param array $objData
 * @param Array (Optional) $attributes
   (index) gridColumns
 *
 * @return String html
 */

function imageGallery($objData){
    $images = $objData->images;
    $galleries = !empty($images)?explode('|',$objData->images):[];
    $layout = '';
    if(count($galleries) >0){
        foreach($galleries as $image){
            $layout .= view('frontend.'.getTheme().'.template-parts.image-gallery.gallery', ['image'=>$image,'gallery'=>$objData])->render();;
        }
    }

    return view('frontend.'.getTheme().'.template-parts.image-gallery.gallery-wrapper', ['imgGallerySlot' => $layout])->render();

}

```
<hr>

```html
@php
    /**
        Template Name: Image Gallery Content
        Attributes:
            1. $image
            2. $gallery->title
    */
@endphp

<div class="project item col-md-6 col-xl-4 velvet">
    <figure class="overlay overlay-1 rounded">
        <a href="{{$image}}" data-glightbox data-gallery="shots-group">
            <img class="img-thumbnail" src="{{$image}}" alt="" />
        </a>
        <figcaption>
            <h5 class="from-top mb-0">{{$gallery->title}}</h5>
        </figcaption>
    </figure>
</div>

```

<hr>

##### Image Gallery wrapper

```html
<section id="portfolio">
    <div class="wrapper ">
        <div class="container py-15 py-md-17 text-center">
            <div class="row mb-5">
                <div class="col-md-10 col-xl-9 col-xxl-7 mx-auto text-center">
                    <h2 class="fs-15 text-uppercase text-primary mb-3">Our Gallery</h2>
                    <h3 class="display-4 mb-3 px-lg-14">Sharing Hope Through Powerful Image Stories.</h3>
                </div>
                <!--/column -->
            </div>
            <!--/.row -->
            <div class="grid grid-view projects-masonry">
                <div class="row gx-md-6 gy-6 isotope">
                    {!! $imgGallerySlot !!}
                </div>
                <!-- /.row -->
            </div>
            <!-- /.grid -->
        </div>
        <!-- /.container -->
    </div>
    <!-- /.wrapper -->
</section>

```
<hr>

### Video Gallery

<hr>

```php


/* * * *
 * Return gallery Videos html
 * @param array $objData
 * @param Array (Optional) $attributes
   (index) gridColumns
 *
 * @return String html
 */

function videosGallery($objData ){
    $videos = json_decode($objData->link);

    $layout = '';
    if(count($videos) >0){
        foreach($videos as $video){
            $layout .= view('frontend.'.getTheme().'.template-parts.video-gallery.video', compact(['video','objData']))->render();
        }
    }
    return view('frontend.'.getTheme().'.template-parts.video-gallery.video-wrapper', ['videoGallerySlot' => $layout])->render();

}


```

<hr>


```html
@php
    /**
        Template Name: Video Gallery Content
        Attributes:
            1. $video
            2. $objData->title
    */
@endphp

<div class="col-sm-4 col-4 col-md-4 col-lg-4 pt-4">
    <div class="video-widget ">
        <iframe width="100%" height="315" src="{{$video}}" title="{{$objData->title}}" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        <figcaption>
            <h5 class="from-top mb-0">{{$objData->title}}</h5>
        </figcaption>
    </div>
</div>


```

##### Video Gallery Wrapper

<hr>

```html

<section id="portfolio">
    <div class="wrapper bg-gray">
        <div class="container py-15 py-md-17 text-center">
            <div class="row mb-5">
                <div class="col-md-10 col-xl-9 col-xxl-7 mx-auto text-center">
                    <h2 class="fs-15 text-uppercase text-primary mb-3">Our Gallery</h2>
                    <h3 class="display-4 mb-3 px-lg-14">Sharing Hope Through Powerful Image Stories.</h3>
                </div>
                <!--/column -->
            </div>
            <!--/.row -->
            <div class="grid grid-view projects-masonry">
                <div class="row gx-md-6 gy-6 isotope">
                    {!! $videoGallerySlot !!}
                </div>
                <!-- /.row -->
            </div>
            <!-- /.grid -->
        </div>
        <!-- /.container -->
    </div>
    <!-- /.wrapper -->
</section>


```


### Album 

<hr>

```php


/* * * *
 * Return gallery image html
 * @param  (Optional) $galleryNum
 *
 * @return String html
 */

function galleryAlbum($galleryNum =''){


    $albums = Content::galleryAlbum($galleryNum);
    $layout = '';
    if (!empty($albums)) {
        foreach ($albums as $gallery) {
            $images = !empty($gallery->images) ? explode('|', $gallery->images) : [];
            $layout .= view('frontend.'.getTheme().'.template-parts.gallery-album.album', compact(['gallery','images']))->render();
        }
    }
    return view('frontend.'.getTheme().'.template-parts.gallery-album.album-wrapper', ['albumSlot' => $layout, 'albums'=> $albums])->render();

}


```

<hr>

```html

@php
    /**
        Template Name: Gallery Album Content
        Attributes:
            1. $gallery->title
            2. $gallery->alias
            3. $gallery->description
            4. count($images) // total image count
            5. viewImage($gallery->images,['withTag'=>false]); // without tag only image link
            6. viewImage($gallery->images); // with img tag
    */
@endphp
<div class="project item col-md-6 col-xl-3 velvet">
    <div class="card mb-4 box-shadow">
        <a href="{{url('gallery/'.$gallery->alias)}}">
            <img class="card-img-top" height="250" src="{{viewImage($gallery->images,['withTag'=>false])}}" alt="Card image cap">
            <div class="text-center p-2">
                <h3 class="mb-0">{{$gallery->title}}</h3>
                <p class="card-text mb-0">{{$gallery->description}}</p>
                <small class="text-muted">{{count($images)}}</small>
            </div>
        </a>
    </div>
</div>

```

<hr>

##### Album Wrapper

```html

<section id="portfolio">
    <div class="wrapper bg-gray">
        <div class="container py-15 py-md-17 text-center">
            <div class="row mb-5">
                <div class="col-md-10 col-xl-9 col-xxl-7 mx-auto text-center">
                    <h2 class="fs-15 text-uppercase text-primary mb-3">Our Gallery</h2>
                    <h3 class="display-4 mb-3 px-lg-14">Sharing Hope Through Powerful Image Stories.</h3>
                </div>
                <!--/column -->
            </div>
            <!--/.row -->
            <div class="grid grid-view projects-masonry">
                <div class="row gx-md-6 gy-6 isotope">
                    {!! $albumSlot !!}
                </div>
                <!-- /.row -->
            </div>
            <!-- /.grid -->
        </div>
        <!-- /.container -->
    </div>
    <!-- /.wrapper -->
</section>

```