  Reusable Template Layouts
  <hr>

  - [Header Template](layouts/header-tmpl.md)
  - [Menu Template](layouts/menu-tmpl.md)
  - [Home Template](layouts/home-tmpl.md)
  - [Banner/Slider Template](layouts/banner-tmpl.md)
  - [Blog Post Template](layouts/blog-tmpl.md)
  - [Gallery Template](layouts/gallery-tmpl.md)
  - [Service Template](layouts/service-tmpl.md)
  - [Team Template](layouts/team-tmpl.md)
  - [Theme](layouts/theme-tmpl.md)
  - [Video Gallery](layouts/video-tmpl.md)
  - [Footer Template](layouts/footer-tmpl.md)





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


## Blog

```php
<div class="container-fluid" style="margin-top:20px">
	<div class="container">
		<div class="row">
				<!--<h2 class="section-title">From The Blog</h2>-->				
				<?php  																			
					  if(isset($blog_cat) && !empty($blog_cat) ):	
					 	$s=1;
						foreach($blog_cat as $item):
							
							$string = $item['created_at'];
							$timestamp = strtotime($string);
							
							echo '<div class="col-md-4"><article class="blog-item"><div class="blog-thumbnail">';

							echo featuredimg($item['featuredimg'],$item['title']);

							echo '<div class="blog-date"> <p class="day">'.date("d", $timestamp).'</p><p class="monthyear">'.date("M", $timestamp).' '.date("Y", $timestamp).'</p></div></div>';

							echo '<div class="blog-content"><h4 class="blog-title"><a href="'.base_url('blog/'.$item['alias']).'">'.$item['title'].'</a></h4>';

							//echo '<p class="blog-meta">By: <a href="#">admin</a> | Tags: <a href="#">Graphic</a>, <a href="#">illustration</a>, <a href="#">Logo</a></p>';

							echo '<p>'.text_num($item['introtext'], 120).'</p>';
							echo '<a href="'.base_url('blog/'.$item['alias']).'" class="btn btn-default btn-mini">READ MORE &nbsp;<i class="fa fa-angle-right"></i></a></div></article></div>';
																											
							$s++;		  			  
						endforeach;
						
					endif;	
				?>					
	    </div>
    </div>
</div>
```

# Sliders

``` html
<?php if($home && isset($slider_cat) && !empty($slider_cat)): ?>
<div class="container-fluid slider-one">
    <div class="row">
        <div id="carousel" class="carousel slide carousel-fade" data-ride="true" data-interval="false" >
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

