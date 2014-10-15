---
layout: post
title: "Bourbon, made the way you like it."
date: 2014-10-15 00:45:00
categories: programming
---

## Bourbon ##

Such interesting naming by these programmers. I suppose **Bourbon** **Neat** and **Bitters**, then asking for **Refills** pass as programming humor. Bourbon is a mixin library for Sass. It is much like compass, but it is supposed to be much more lightweight. Compass is robust, but it is layered, and some functionalities takes too long to load. Bourbon should be much more interesting and fun to use.

Neat, Bitters, and Refills are build upon Bourbon. Bourbon works by itself, or in conjunction with one, two or all three of them. Bourbon competes with the famous Bootstrap. Bourbon itself is limited, but with the addition of Neat, Bitters, and Refills, it becomes a powerful Sass framework. Also, it is written in Ruby, so it has native Rails support (+1).

[Neat](http://neat.bourbon.io/) is a grid framework, similar to Bootstrap's grid framework. But again, its goal is to be lightweight. Neat works by applying styles to HTML tags, different from Bootstrap which is done by attributes on HTML tags.

[Bitters](http://bitters.bourbon.io/) provides some basic styling. Compared to Bootstrap, it does a lot less. It also isn't has padding heavy as Bootstrap. I found Bootstrap to look very bulky and fat. While Bitters adds some styling, but is still very minimal.

[Refills](http://refills.bourbon.io/) are packaged patterns and components. I haven't looked into it much. From first look, it offers a variety of functionality and visual effects. The examples look modern and minimal. I look forward to building web views using Refills.

## Installation ##

Installation wasn't that easy because something weird happened to my files. But it is fairly straight forward. I'm only going to list the method to add Bourbon and the others to Rails apps. Because that's what they were originally build for. They can just as easily be moved to a different app, though.

Add the Bourbon, Neat, Bitters, Refills gem to Gemfile
{% highlight ruby %}
gem 'bourbon'
gem 'neat'
gem 'bitters'
gem 'refills'
{% endhighlight %}

Install them by going to the root directly and run
{% highlight bash %}
bundle install
{% endhighlight %}

If you are using .rbenv to manage ruby versions, you need to do `rbenv rehash`

Now install Bourbon into `stylesheets` directory<br />
Change directory to `/app/assets/stylesheets` and install them there
{% highlight bash %}
$ cd myApp/app/assets/stylesheets
$ bourbon install
# Bourbon files installed to bourbon/
$ neat install
# Neat files installed to neat/
$ bitters install
# Bitters files installed to base/base
{% endhighlight %}

Refills components can be installed by running `rails refills:import SNIPPET` where `SNIPPET` is the component/pattern to be added

After installing the files, change all the stylesheets to the extension `.css.scss`. This tells rails to preprocess these files using Sass preprocessor first then as css.

Go into `application.css.scss` and remove everything. You won't be using Sprockets (Asset Pipeline) to load the css files. Because by using rails's asset pipeline, it compiles each Sass file individually, so you can't really use the mixins and variables in Bourbon. So instead of Sprockets, use Sass's `@import`

{% highlight sass %}
// application.css.scss

// @import "normalize-rails";

@import "bourbon/bourbon";
@import "base/base";
@import "neat/neat";

// rest of the sass stylesheets

{% endhighlight %}

It's important to remember to load Bitters `base/base` before Neat. `@import normalize-rails` is recommended, you can do so by adding `gem 'normalize-rails'` to Gemfile.

Also uncomment `// @import "grid-settings";` in `base/_base.scss`, so it can be used with Neat.

That's pretty much it. All the mixins and variables and whatnot should be available.

Remember, if you are going to deploy the app, double check `application.css.scss` to make sure it has all the `@import`. And precompile the Sass file then deploy.