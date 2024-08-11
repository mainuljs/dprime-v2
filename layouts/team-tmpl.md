### Team layout

```php

/* * * *
 * Team
 * @param String Optional $catAlias
 * @param number Optional $teamNum
 *
 * @return String html
 */

function team($catAlias='', $teamNum=''){
    $teams = Content::teams($catAlias, $teamNum);
    $layout = '';
    if (!empty($teams)){
        foreach ($teams as $team){
            $socialLink = json_decode($team->social_link);
            $data = [
                'team'          => $team,
                'socialLink'    => $socialLink,
                'teamAlias'     => getCleanUrl($team->name)
            ];
            $layout .= view('frontend.'.getTheme().'.template-parts.team.team', $data)->render();
        }
    }
    return view('frontend.'.getTheme().'.template-parts.team.team-wrapper', ['teamSlot' => $layout, 'teams'=> $teams])->render();

}

```

<hr>

```html

@php
    /**
        Template Name: Team Content
        Attributes:
            1. $team->name
            2. $team->designation
            3. $team->contact
            4. $team->email
            5. viewImage($team->image,['withTag'=>false]); // without tag only image link
            6. viewImage($team->image); // with img tag
            7. $teamAlias; // team alias  use example <a href="{{url('team/'$teamAlias)}}"></a>
            8. $socialLink // object for loop example
            @ if(!empty($socialLink))
                @foreach($socialLink as $socialMedia)
                <a href="{{$socialMedia->socialLink}}" ><i class="{{ $socialMedia->socialId }} text-base-color"></i></a>
                @endforeach
            @endif
    */
@endphp

<div class="col-12 col-md-6 col-lg-3 mb-5">
    <div class="card border-0 border-bottom border-primary shadow-sm overflow-hidden">

        <div class="card-body p-0">
            <figure class="m-0 p-0">
                <img class="img-fluid" loading="lazy" src="{{viewImage($team->image, ['withTag'=>false])}}" alt="">
                <figcaption class="m-0 p-4">
                    <h4 class="mb-1">{{ $team->name }}</h4>
                    <p class=" mb-0"> {{ $team->designation }}</p>
                    <p class="text-secondary mb-0">{{ $team->contact }} </p>
                    <p class="text-secondary mb-0">{{ $team->email }}</p>
                </figcaption>
            </figure>
        </div>
    </div>
</div>




```
<hr>

```html
<section class="bg-light py-3 py-md-5 py-xl-8">
    <div class="container">
        <div class="row justify-content-md-center">
            <div class="col-12 col-md-10 col-lg-8 col-xl-7 col-xxl-6">
                <h2 class="mb-4 display-5 text-center">Our Team</h2>
                <h4 class=" text-center">We are a group of innovative, experienced, and proficient teams. You will love to collaborate with us.</h4>
            </div>
        </div>
    </div>

    <div class="container overflow-hidden">
        <div class="row gy-4 gy-lg-0 gx-xxl-5">
            {!! $teamSlot !!}
        </div>
    </div>
</section>

```html