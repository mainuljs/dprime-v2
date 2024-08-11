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


### Search Box

<hr>

```html
<!-- top search -->
<div class="col col-md-1 search-col">		
    <div class="top-search">
		<a href="#"><span class="material-icons">search</span></a>
		<div class="search-box">
			<form action="<?php echo base_url('search'); ?>" method="post" class="form-inline">
				<div class="input-group flex-fill">
					<input type="text" name="key_word" class="form-control" placeHolder="Your Keyword" />				
					<div class="input-group-append">
					    <button class="btn btn-info" type="submit">Go</button>
					</div>	
				</div>				
			</form>													
		</div>
	</div>		  
</div>
<!-- end: top search-->
```

