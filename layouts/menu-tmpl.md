
### Menu Layouts

<hr>

### Menu Bar

<hr>

#####

```html

<nav class="navbar navbar-expand-lg bg-light">
  <div class="container-fluid">  
    <div class="collapse navbar-collapse" id="navbarNav">
      
		 @php
            $attributes = [
              'navAttr'          => 'class="navbar-nav ml-auto"', //<ul class="navbar-nav"> 
			  'subNavAttr'       => 'class="nav-item dropdown"', //<li class="nav-item dropdown">
			  'itemAttr'		 => 'class="nav-item"', //<li class="nav-item">
			  'itemLinkAttr'     => 'class="nav-link"', // <a class="nav-link">
			  'drowDownAttr'     => 'class="dropdown-menu"', //<ul class="dropdown-menu">
			  'dropDownLinkAttr' => 'class="nav-link dropdown-toggle" data-bs-toggle="dropdown" href="#"', //<a class="class="nav-link dropdown-toggle" data-bs-toggle="dropdown" href="#"">
			  'activeItemAttr'   => 'class="active"',
            ];
          @endphp
		  
          {!! showMainMenu($menus, $attributes) !!}
	  
	 
    </div>
  </div>
</nav>

```


```html

```



##### Navbar - Full Menu Bar

 - With logo, main menu, responsive menu, action button

<hr>

```html
<nav class="navbar navbar-expand-lg center-nav transparent navbar-light">
             <div class="container flex-lg-row flex-nowrap align-items-center">			 
			 
                 <div class="navbar-brand w-100">
                     <a href="{{url('/')}}">
                         <img height="60" src="{{$logo}}" srcset="{{$logo}}" alt="{{$appName}}" />
                     </a>
                 </div>
				 
				 
                 <div class="navbar-collapse offcanvas offcanvas-nav offcanvas-start">
				 
                     <div class="offcanvas-header d-lg-none">
                         <img height="78" class="mb-4" src="{{$logo}}" srcset="{{$logo}}" alt="{{$appName}}" />
                         <button type="button" class="btn-close btn-close-white" data-bs-dismiss="offcanvas" aria-label="Close"></button>
                     </div>
					 
					 
                     <div class="offcanvas-body ms-lg-auto d-flex flex-column h-100">
                     @php
                         $attributes = [
                             'subNavAttr'        => 'class="dropdown-menu"',
                             'dropDownLiA'      => 'class="dropdown-item"'
                         ];
                     @endphp
                     {!! showMainMenu($menus, $attributes) !!}					 

                     <!-- /.navbar-nav -->
					 
					 
                         <div class="offcanvas-footer d-lg-none">
                             <div>
                                 @php
                                     $allEmails = explode(',', $email);
                                     $socialMedia = json_decode($social, true);
                                 @endphp
                                 <a href="mailto:{{$allEmails[0]}}" class="link-inverse">{{$allEmails[0]}}</a>
                                 <br /> {{$contact}} <br />
                                 <nav class="nav social social-white mt-4">
                                     @if(!empty($socialMedia))
                                         @foreach($socialMedia as $key=>$sMedia)
                                             @php
                                                 $sIcon = strtolower($sMedia['network_name']);
                                                 if ($sIcon =='facebook'){
                                                   $sIcon = $sIcon.'-f';
                                                 }
                                             @endphp
                                             <a href="{{$sMedia['network_link']}}"><i class="uil uil-{{$sIcon}}"></i></a>
                                         @endforeach
                                     @endif
                                 </nav>
                                 <!-- /.social -->
                             </div>
                         </div>
                         <!-- /.offcanvas-footer -->
                     </div>
                     <!-- /.offcanvas-body -->
                 </div>


                 <div class="navbar-other w-100 d-flex ms-auto">
                     <ul class="navbar-nav flex-row align-items-center ms-auto">
                         <li class="nav-item d-none d-md-block">
                             <a href="{{url('/contact')}}" class="btn btn-sm btn-primary rounded-pill">Book A Trip</a>
                         </li>
                         <li class="nav-item d-lg-none">
                             <button class="hamburger offcanvas-nav-btn"><span></span></button>
                         </li>
                     </ul>
                         <!-- /.navbar-nav -->
                 </div>
             </div>
             <!-- /.container -->
         </nav>
```
