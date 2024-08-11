### Top Header
<hr>

```html
<!-- top header -->
<section class="container-fluid top-header-two">
	<div class="container">
		<div class="row">
			<div class="col-4 col-md-3 head-icon">
				<a href="#"><span class="fa fa-facebook"> </span> </a>
				<a href="#"><span class="fa fa-twitter"> </span> </a>
				<a href="#"><span class="fa fa-linkedin"> </span> </a>
			</div>
		    <div class="col-8 col-md-9 last pl-0">
				<span class="fa fa-phone"></span><a class="" href="tel:2123865575"> 212 386 5575</a>&nbsp;&nbsp;&nbsp;
				<span class="fa fa-envelope"> </span> admin@email.com
			</div>
		</div>
	</div>
</section>
<!-- end: top header --->
```

<hr>

### Main Menu
<hr>

```html
<!-- main menu -->
<div class="col col-md-9 menu-col">		  		 
    <nav class="navbar navbar-expand main-menu">				  
	    <div class="collapse navbar-collapse justify-content-end top-nav">		
			<?php
				showMainMenu($menuArray, array('submenu'=>FALSE), segment(1));
			?>
	    </div>																
    </nav>
</div>
<!-- end: main menu-->
```
