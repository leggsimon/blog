---
layout: post
title:  "Welcome to Jekyll!"
date:   2015-10-20 22:36:05
categories: jekyll update
---
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

```ruby
def foo bar
  return bar
end
```

```js
var getCityTemperature = function(city) {
  console.log(city)
  var url = "http://api.openweathermap.org/data/2.5/weather?q=" + city + "&APPID=b3e354ab2227f3e98542190461b7fe44&units=metric"
  var response = $.get(url).done(function() {
    $('#cityWeather').html("Current temperature: " + response.responseJSON.main.temp + "&#x2103")
  })
}
```
This is Ruby:
{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end

print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.

def foo bar
  puts bar
end
{% endhighlight %}

This is javascript
{% highlight javascript %}
var getCityTemperature = function(city) {
  console.log(city)
  var url = "http://api.openweathermap.org/data/2.5/weather?q=" + city + "&APPID=b3e354ab2227f3e98542190461b7fe44&units=metric"
  var response = $.get(url).done(function() {
    $('#cityWeather').html("Current temperature: " + response.responseJSON.main.temp + "&#x2103")
  })

}
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
