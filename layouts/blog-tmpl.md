## Blog Post Layout
<hr>

```php


/* * * *
 * Blog or Posts
 * @param String Optional $blogType - recent, popular, featured
   (index) gridColumns
 * @param String Optional $blogCategory
 * @param number Optional $limit
 * @return String html
 */
function blogs($blogType = 'recent', $blogCategory = '', $limit = '3'){
    $blogType = $blogType?$blogType:'recent';
    if($blogType == 'recent'){
        $blogs = Content::recentArticles($limit, $blogCategory);
    }else{
        $blogs = Content::attributedArticles($blogType,$limit);
    }

    $layout = '';
    if (!empty($blogs)){
        foreach ($blogs as $blog ){
            $category = $blog->categories->first();
            $data = [
                'blog'              => $blog,
                'introtext'         => strip_tags($blog->introtext),
                'blogAlias'         => postUrl($blog->alias, $blog->id),
                'categoryAlias'     => url('section'.$category->cat_alias),
                'categoryTitle'     => $category->cat_title
            ];
            $layout .= view('frontend.'.getTheme().'.template-parts.blog.blog', $data)->render();
        }
        return view('frontend.'.getTheme().'.template-parts.blog.blog-wrapper', ['blogSlot' => $layout, 'teams'=> $blogs])->render();

    }

}

```


```html
@php
    /**
        Template Name: Gallery Album Content
        Attributes:
            1. $blog->title
            2. $blogAlias
            3. viewImage($blog->featuredimg, ['title'=> $blog->title])
            4. $categoryAlias
            5. $categoryTitle
            6. text_num($introtext,100)
            7. date('d M Y', strtotime($blog->created_at))
    */
@endphp
<div class="swiper-slide">
    <div class="item-inner">
        <article>
            <div class="card">
                <figure class="card-img-top overlay overlay-1 hover-scale">
                    <a href="{{$blogAlias}}">
                        {!! viewImage($blog->featuredimg, ['title'=> $blog->title]) !!}
                    </a>
                    <figcaption>
                        <h5 class="from-top mb-0">Read More</h5>
                    </figcaption>
                </figure>
                <div class="card-body">
                    <div class="post-header">
                        <div class="post-category text-line">
                            <a href="{{$categoryAlias}}" class="hover" rel="category">{{$categoryTitle}}</a>
                        </div>
                        <!-- /.post-category -->
                        <h2 class="post-title h3 mt-1 mb-3"><a class="link-dark" href="{{$blogAlias}}">{{$blog->title}}</a></h2>
                    </div>
                    <!-- /.post-header -->
                    <div class="post-content">
                        <p>{{ text_num($introtext,100) }}</p>
                    </div>
                    <!-- /.post-content -->
                </div>
                <!--/.card-body -->
                <div class="card-footer">
                    <ul class="post-meta d-flex mb-0">
                        <li class="post-date"><i class="uil uil-calendar-alt"></i>
                            <span>{{date('d M Y', strtotime($blog->created_at))}}</span>
                        </li>
                    </ul>
                    <!-- /.post-meta -->
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

<hr>

```html
<section class="wrapper bg-gray">
    <div class="container py-14 py-md-16">
        <div class="row">
            <div class="col-lg-9 col-xl-8 col-xxl-7 mx-auto">
                <h2 class="fs-15 text-uppercase text-primary text-center">GET INFORMED</h2>
                <h3 class="display-4 mb-6 text-center">LATEST ARTICLES</h3>
            </div>
            <!-- /column -->
        </div>
        <!-- /.row -->
        <div class="position-relative">
            <div class="swiper-container dots-closer blog grid-view mb-6" data-margin="0" data-dots="true" data-items-xl="3" data-items-md="2" data-items-xs="1">
                <div class="swiper">
                    <div class="swiper-wrapper">
                        {!! $blogSlot !!}
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
