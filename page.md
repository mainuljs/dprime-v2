## Article or Post Page Content as Services

### recentArticles() 
<hr>

The `recentArticles()` function retrieves the specified number of recent published articles with the categories relationship from the database. It uses the Laravel Eloquent ORM to make the database query.

##### Parameters 
- `$numberOfArticle` : (optional) - The number of recent articles to retrieve. It defaults to 10 if not specified.
- `$category` : (optional) - Get the articles and posts of a specifice category.

##### Return Value
The function returns a collection of model instances containing the retrieved articles and their associated categories.

##### Example Usage
```
 //get last 4 recent articles 
 @foreach(Content::recentArticles(4) as $item)
    ....
 @endforeach

//for specific cateogry
 @foreach(Content::recentArticles(4, $categoryAlias) as $item)
    ....
 @endforeach

```

<hr>

### attributedArticles() 
<hr>

The `attributedArticles()` provide the attributed article like featured and suggested attribution.

##### Parameters 
- `$attribution` : (optional) - Get `featured` or `suggested` the articles and posts. Default `featured` if not specified.
- `$numberOfArticle` : (optional) - The number of attributed articles to retrieve. It defaults to 10 if not specified.


##### Return Value
Model Collection Instance

##### Example Usage
```
 //get last 4 recent articles 
 @foreach(Content::attributedArticles('featured') as $item)
    ....
 @endforeach

//for specific cateogry
 @foreach(Content::attributedArticles('suggested', 4) as $item)
    ....
 @endforeach

```
<hr>


<hr>

### nextPrev() 
<hr>

The `nextPrev()` provide the attributed article like featured and suggested attribution.

##### Parameters 
- `$articleId` : Article or Post Id for which yout want the next or previous 
- `$nextPrev` : For next `next` and for privious `prev`.
- `$categoryName` : (optional) - for Specific Category

##### Example Usage
```
 //next article or post
 @foreach(Content::nextPrev('10', 'next') as $item)
    ....
 @endforeach

//previous article or post
 @foreach(Content::nextPrev('10', 'prev', 'products') as $item)
    ....
 @endforeach

```

<hr>

### breadcrumb() 
<hr>

The `breadcrumb()` provide the attributed article like featured and suggested attribution.

##### Parameters 
- `$categoryId` : Article or Post Category Id
- `$title` : (Optional) Title for title tag attributes

##### Example Usage
```
 //generate breadcrumb
 {{Content::breadcrumb(2)}}

```
<hr>


