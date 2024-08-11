
## Banner Layout
<hr>

```php

/* * * *
 * Banners
 * @return String html
 */
function banners(){
    $banners = Content::banners();
    $layout = '';
    if (!empty($banners) && count($banners) >0) {
        foreach ($banners as $banner) {
            $layout .= view('frontend.'.getTheme().'.template-parts.banner.banner', compact('banner'))->render();
        }
    }
    return view('frontend.'.getTheme().'.template-parts.banner.banner-wrapper', ['bannerSlot' => $layout])->render();
}

```

<hr>

```html
@php
    /**
        Template Name: banner Template
        Attributes:
            1. $banner->title;
            2. $banner->sub_title;
            3. $banner->link;
            4. $banner->sub_link;
            5. viewImage($banner->images,['withTag'=>false]); // without tag only image link
            6. viewImage($banner->images); // with img tag
    */
@endphp

<div class="swiper-slide bg-overlay bg-overlay-400 bg-dark bg-image" data-image-src="{{viewImage($banner->images,['withTag'=>false])}}">
    <div class="container h-100">
        <div class="row h-100">
            <div class="col-lg-8 col-xl-8 col-xxl-8 mx-auto text-center justify-content-center align-self-center align-items-center">
                <p class="lead  lh-sm  text-primary animate__animated animate__slideInRight animate__delay-1s capi text-uppercase">WELCOME TO {{$appName}}</p>
                <h2 class="display-1 fs-56 mb-4 text-white animate__animated animate__slideInDown animate__delay-1s">{{$banner->title}}</h2>
                <p class="lead fs-24 lh-sm mb-7 text-white animate__animated animate__slideInRight animate__delay-1s">{{$banner->sub_title}}</p>
                <div class="animate__animated animate__slideInUp animate__delay-1s">
                    <span><a href="{{$banner->link}}" class="btn btn-md btn-primary rounded-pill me-2">Read More</a></span>
                    <span><a href="{{$banner->sub_link}}" class="btn btn-md btn-orange rounded-pill">Contact Us</a></span>
                </div>
            </div>
            <!--/column -->
        </div>
        <!--/.row -->
    </div>
    <!--/.container -->
</div>

```
<hr>

```html
<section class="wrapper bg-dark">
    <div class="swiper-container swiper-hero dots-over" data-margin="0" data-autoplay="true" data-autoplaytime="7000" data-nav="true" data-dots="false" data-items="1">
        <div class="swiper">
            <div class="swiper-wrapper">
                {!! $bannerSlot !!}
            <!--/.swiper-slide -->
            </div>
            <!--/.swiper-wrapper -->
        </div>
        <!-- /.swiper -->
    </div>
    <!-- /.swiper-container -->
</section>
```




<hr>





## Carousel

```html
<?php if($home && isset($slider_cat) && !empty($slider_cat)): ?>
<div class="container-fluid slider-one">
    <div class="row">
        <div id="carousel" class="carousel slide carousel-fade" data-ride="true" data-interval="false" style="width: 100%;">
            <ol class="carousel-indicators">
				<?php 
				   	$i = 0;
				   	foreach($slider_cat[0] as $slide ):
						if($i == 0):
							echo '<li data-target="#carousel" data-slide-to="'.$i.'" class="active"></li>';		
						else:
						 	echo '<li data-target="#carousel" data-slide-to="'.$i.'"></li>';
						endif;
						$i++;
					endforeach;
				?>		
             </ol>
	  
	        <div class="carousel-inner">         
				<?php 
				 	count($slider_cat);
				 		
					foreach($slider_cat as $slide ):
					$cnt_slide = 1;
					$cnt_slide1 = 1;
					if( is_array($slide) ):
						foreach($slide as $sld):
							if($cnt_slide == 1):
								echo '<div class="carousel-item active">';
							else:
								echo '<div class="carousel-item">';
							endif;
							
							echo '<img class="d-block" src="'.$sld['featuredimg'].'" alt="'.$sld['title'].'" />';

							echo '<div class="carousel-caption d-md-block"><h3 class="animate__animated animate__slideInDown">'.$sld['title'].'</h3><p>'.$sld['introtext'].'</p><br />';

							echo '<a class="btn btn-default animate__animated animate__slideInUp" href="'.base_url($sld['alias']).'">View <i class="material-icons">keyboard_arrow_right</i></a></div>';								
							
							echo '</div>';
									
							$cnt_slide++;	
																		
						endforeach;	
					 endif;
					endforeach;
				?> 
            </div>
                                                
		    <a class="carousel-control-prev" href="#carousel" role="button"  data-slide="prev">
		        <span class="fa fa-chevron-left" aria-hidden="true"></span>
		        <span class="sr-only">Previous</span>
		    </a>
		    <a class="carousel-control-next" href="#carousel" role="button"  data-slide="next">
		        <span class="fa fa-chevron-right" aria-hidden="true"></span>
		        <span class="sr-only">Next</span>
		    </a>
        </div>
	</div>
</div>

<?php endif; ?>  
```