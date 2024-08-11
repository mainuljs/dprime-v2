### Service Layout
<hr>

```php

/* * * *
 * Services
 * @param String Optional $blogCategory
 * @param number Optional $limit
 *
 * @return String html
 */
function blogService($blogCategory = '', $limit = '4'){
    $blogs = Content::recentArticles($limit, $blogCategory);

    $layout = '';
    if (!empty($blogs)){
        foreach ($blogs as $blog ){
            $category = $blog->categories->first();
            $pageAttributes = json_decode($blog->page_attributes, true);
            $pageAttributes = array_column($pageAttributes, 'value', 'name');
            $data = [
                'data'              => $blog,
                'introtext'         => strip_tags($blog->introtext),
                'blogAlias'         => postUrl($blog->alias, $blog->id),
                'categoryAlias'     => url('section'.$category->cat_alias),
                'categoryTitle'     => $category->cat_title,
                'pageAttributes'    => $pageAttributes,
            ];

            $layout .= view('frontend.'.getTheme().'.template-parts.service.service', $data)->render();
        }
        return view('frontend.'.getTheme().'.template-parts.service.service-wrapper', ['blogServiceSlot' => $layout, 'teams'=> $blogs])->render();

    }

}

```

<hr>

```html

@php
    /**
        Template Name: Blog Serve Content
        Attributes:
            1. {{$data->title}}
            2. {{$pageAttributes['price']??''}}
            3. {{$pageAttributes['old_price']??''}}
            4. {!!viewImage($data->featuredimg, ['title'=> $data->title])!!}
            5. $categoryTitle
            6. {{$pageAttributes['days_night']??''}}
            7. {!! $data->introtext !!}
            8. {{ postUrl($data->alias, $data->id) }}

    */
@endphp

<div class="swiper-slide">
    <div class="item-inner">
        <article>
            <div class="card">
                <figure class="card-img-top overlay overlay-1 hover-scale">
                    <a href="{{ postUrl($data->alias, $data->id) }}">
                        {!!viewImage($data->featuredimg, ['title'=> $data->title])!!}
                    </a>
                </figure>
                <div class="card-body">
                    <div class="post-header">
                        <div class="post-category ">
                            <a href="#" class="hover" rel="category">
                                <span class="h6 text-primary">{{$pageAttributes['price']??''}} </span> <del>{{$pageAttributes['old_price']??''}} </del>
                            </a>
                        </div>
                        <!-- /.post-category -->
                        <h2 class="post-title h3 mt-1 mb-3">
                            <a class="link-dark" href="{{ postUrl($data->alias, $data->id) }}">{{$data->title}}</a>
                        </h2>
                    </div>
                    <!-- /.post-header -->
                    <div class="post-content">
                        <p><i class="uil uil-clock text-primary"></i> {{$pageAttributes['days_night']??''}} </p>
                        <div class="list-area">
                            {!! $data->introtext !!}
                        </div>
                    </div>
                    <!-- /.post-content -->
                </div>
                <!--/.card-body -->
                <div class="card-footer">
                    <span><a href="{{ postUrl($data->alias, $data->id) }}" class="btn btn-sm btn-primary rounded-pill">Explore Now</a></span>
                </div>
                <!-- /.card-footer -->
            </div>
            <!-- /.card -->
        </article>
        <!-- /article -->
    </div>
    <!-- /.item-inner -->
</div>

```
##### Service Layout
<hr>

```html

<section class="wrapper bg-gray">
    <div class="container py-14 py-md-16">
        <div class="row">
            <div class="col-lg-9 col-xl-8 col-xxl-7 mx-auto">
                <h2 class="fs-15 text-uppercase text-primary text-center">CHOOSE YOUR TOUR</h2>
                <h3 class="display-3 mb-6 text-center">Get The Best Plans For Your’s</h3>
            </div>
            <!-- /column -->
        </div>
        <!-- /.row -->
        <div class="position-relative">
            <div class="shape bg-dot primary rellax w-17 h-20" data-rellax-speed="1" style="top: 0; left: -1.7rem;"></div>
            <div class="swiper-container dots-closer blog grid-view mb-6" data-margin="0" data-dots="true" data-items-xl="3" data-items-md="2" data-items-xs="1">
                <div class="swiper">
                    <div class="swiper-wrapper">
                       {!! $blogServiceSlot !!}
                    <!--/.swiper-slide -->

                    </div>
                    <!--/.swiper-wrapper -->
                </div>
                <!-- /.swiper -->
            </div>
            <!-- /.swiper-container -->
        </div>
        <!-- /.position-relative -->
    </div>
    <!-- /.container -->
</section>


```