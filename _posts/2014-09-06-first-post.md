---
layout: post
title:  "This is my first post!"
date:   2014-09-06 23:48:04
categories: jekyll first
---

_Note: this is meant to be a somewhat guide to getting started with posting using Jekyll and with Markdown_

This is the first in `Jekyll`, and the very first markdown I ever written. With the `YAML Front Matter`, I can name, date, and cateogrize this page.

{% highlight yaml %}
---
layout: post
title:  "This is my post!"
date:   2014-09-06 23:48:04
categories: jekyll first
---	
{% endhighlight %}

After writing this post, I can run `jekyll build` to build my website. This will add this markdown post to `_site` directory.

The `_config.yml` file includes all the global configuration settings. Go to [jekyll configuration page][jekyll-config] to find all the configuration options. There are many "variables" that are not on that site. These variables can be used in your pages and posts. For example, `twitter-username` are used in `footer.html` to set up link to your twitter account. Also, it is interesting to note that the icons are drawn using svg.

### Markdown, Textile, Liquid, Redcarpet, kramdown, etc.###

These names are still quite confusing to me. As of the date of writing, this is my understanding. Markdown and textile are both a markup language that transforms into HTML. Liquid is a templating system Jekyll uses, it has nothing to do with the other ones. Redcarpet and kramdown are markup processors. Redcarpet renders textile, and kramdown renders markdown. Kramdown also supports LaTex math. I can probably use that for math/cs notes.

### Embed Images ###
![This is an imagine]({{site.url}}/assets/myface.jpg "This is the imagine title").

`![Alt text]({ {site.url} }/assets/file.ext)` embeds an image from `{ {site.url} }/assets/myface.jpg` is where that image is stored. Do note the usage of `{ {site.url} }`. Liquid automatically transform the double bracket site.url to the variable from `_config.yml`.

Now of course markdown doesn't have a way of specifying image sizes. I definitley don't want my face to be that big. So I'll have to resort to `<img>` tags like so 
<img src="{{site.url}}assets/myface.jpg" height="50px" />

### Links ###
Links are almost identical to images.
You can try `<http://simplehtmlembed.com>`. Email is the same
Or do `[url name](http://website.name)`. It is all the same

### Back to the Basics ###

	* list
	* list
	* list

	1 ordered
	2 ordered
	3 ordered

	*italics*
	_italics_
	**bold**
	__bold__

	Code block is done by tabbing
	Or done with { % highlight lang % } { % endhighlight % } 
		(ignore the spaces between { and %, liquid replaces them)

	Inline code is done with ` and `. It is [SHIFT] + ~ the key next to 1

	hr is ---

	# h1 #
	## h2 ##

[jekyll-config]: http://jekyllrb.com/docs/configuration/
