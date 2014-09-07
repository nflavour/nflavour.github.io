---
layout: post
title:  "This is my first post!"
date:   2014-09-06 23:48:04
categories: jekyll first
---

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

The `_config.yml` file includes all the global configuration settings. Go to [jekyll configuration page] to find all the configuration options. There are many "variables" that are not on that site. These variables can be used in your pages and posts. For example, `twitter-username` are used in `footer.html` to set up link to your twitter account. Also, it is interesting to note that the icons are drawn using svg.

### Markdown, Textile, Liquid, Redcarpet, kramdown, etc.###

These names are still quite confusing to me. As of the date of writing, this is my understanding. Markdown and textile are both a markup language that transforms into HTML. Liquid is a templating system Jekyll uses, it has nothing to do with the other ones. Redcarpet and kramdown are markup processors. Redcarpet renders textile, and kramdown renders markdown. Kramdown also supports LaTex math. I can probably use that for math/cs notes.

[jekyll configuration page]: http://jekyllrb.com/docs/configuration/
