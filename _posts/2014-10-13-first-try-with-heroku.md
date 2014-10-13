---
layout: post
title:  "First time with Heroku?"
date:   2014-10-13 02:49:00
categories: programming
---

So after looking through the services, it seems that everyone recommends heroku as a good PaaS. It's also free for the super basic service. (:

Of course, the first thing I did was try to install redmine. I really wanted a permanent issue tracking for my projects. I could leave it on my computer and do `rails server` every time I want to add/update an issue. But that seems pretty boring (I might as well just use posted notes). 

Setting up redmine locally was very easy. All it took was edit `database.yml` and do `bundle install --without rmagick`. Create a database in mysql and done.

I cannot say it was easy to set up on Heroku. There are lots of confusing steps. Especially the whole thing with `Gemfile` and `Gemfile.lock`. There was a point where I couldn't to push to heroku because my `Gemfile.lock` had gems that didn't match Gemfile. Honestly, I'm still new to Ruby, so I have no idea what's going on.

However thanks to this [guide](href="http://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_(%3E_25x)_on_Heroku") I got through it.

Every step in the guide is as important as another.

Here's a copy of the guide just in case it ever disappears.
<ol>
  <li> `git clone https:..github.com/redmine/redmin.git` or wherever the latest redmine version is hosted </li>
  <li> `git checkout 2.5-stable` or whatever the latest stable version is </li>
  <li> `cd redmine` </li>
  <li> remove the follow from `.gitignore`
{% highlight ruby %}
Gemfile.lock
Gemfile.local
public/plugin_assets
config/initializers/session_store.rb
config/initializers/secret_token.rb
config/configuration.yml
config/email.yml 
{% endhighlight %} </li>
  <li> Heroku seems to love postgresql. Not sure why... Do not edit database.yml, so ignore *"Please configure your config/database.yml first"*. Heroku actually builds database.yml with the proper cloud information</li>
  <li> `bundle install` </li>
  <li> `rake generate_secret_token` </li>
  <li> `heroku create` </li>
  <li> remove `exit 1` at line 10 from `config/environment.rb` </li>
  <li> remove add `config.assets.initialize_on_precompile = false` between line 13 and line 14 to `config/application.rb` <br />
  Should look like this
{% highlight ruby %}
...
12: module RedmineApp
13:   class Application < Rails::Application
14:     config.assets.initialize_on_precompile = false
15:     # Settings in config/environments/* take precedence over those specified here.
...
{% endhighlight %}
  </li>
  <li> Commit the changes
{% highlight bash %}    
git add -A
git commit -m “preparing for heroku”
git push heroku 2.5-stable:master
{% endhighlight %}
  </li>
  <li> Run a few things on heroku side
{% highlight bash %}
heroku run rake db:migrate
heroku run rake redmine:load_default_data
{% endhighlight %}
  </li>
</ol> 

If you are going to use unicorn or something other than webrick (you probably shouldn't use webrick for production server) be sure you follow the proper procedures e.g. [unicorn](href="https://devcenter.heroku.com/articles/rails-unicorn#the-unicorn-server")

Remember to always run `bundle install` before pushing.

*** Do not attempt to try to get github repo to integrate properly. It follow the steps from github_hook, I did get the webhook request to work, but redmine would not display the repo. I think it might have something to do with permissions in Heroku's server. I just gave up on that, and focus on managing the projects.