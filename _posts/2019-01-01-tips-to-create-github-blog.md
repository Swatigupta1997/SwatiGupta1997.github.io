---
layout: default
title: Creating your own blog series
dates: 2019-01-01 15:30 IST
comments: true
---
# Creating a blog using Github and Jkyell
{{ page.dates }}

Hello all!

I will kickstart with something that forms the very basis of this blog series. Yes, you guessed it right! <b><center>How to create a blog using Github (and Jekyll).</center></b>

You must be wondering, why Github? Why not the many blogging websites available online (blogger, wordpress, medium etc.), which offer an extremely simple setup and smooth GUI experience. A lot less time spent on logistics right? 
Well, for one, we are coders! Second, the whole point of this exercise is to explore and learn! So, why not learn how to actually create a blog from scratch as the starting point? Github is great in this aspect, as you will actually need to get your hands dirty, and understand how to use Jekyll. 
Another personal reason is that using Github keeps all my things in one place, as the rest of my work is on git as well, and this can be just one more repo.

So, Lets get down to buisness!

One easy way is to pull the repo by barryclark (https://github.com/barryclark/jekyll-now) and follow his instructions on minimally editing the repo to make it your own. While this is great for someone who doesnot want to spend time demistifying the logistics, again, that is not the point of this exercise.

So we will create our blog from scratch. (With guidance from barry clark ofc!)

PreRequisites:
Not many, just be comfortable using Github, and basic html coding.

Some important details:
- hey, What's Jekyll? : Jekyll is a parsing engine (written in ruby by Github's cofounder) used to build static websites from dynamic components such as templates, partials, liquid code, markdown, html, css etc. Jekyll is known as "a simple, blog aware, static site generator".
- We are not going to atempt something fancy here. If you are good with html/css, go ahead and add fancier elements to the blog/website. I will be using one of the already available themes.
- At any point, if you have a doubt, feel free to browse through my repo and see what to do yourself! Else, comment below!

- Step 1: Create your repository with the name: <username>.github.io 
- Step 2: create default directory structure:
          - _posts/
          - _layouts/
          - _config.yml
          -  index.md
  
 Explanation:
index.md is the default landing page when '<username>.github.io' is visited via url. You can directly make it your blog homepage or you can make this your personal website (like I did) and add a link to another page which can be your blog homepage (ref blog_home.html).</br>
_config.yml is the YAML file with all the configuration details.
_posts/ directory is where your blog entries will be kept. naming convention for each blog entry: <year>-<month>-<date>-<title>.md (Ex: 2019-01-01-tips-to-create-github-blog.md)
_layouts/ directory is where you will put your html layouts. you can have as many as you like, i will only be using one, called 'default.html'
  
# Update in progress. Hang on!




{% if page.comments %}
<div id="disqus_thread"></div>
<script>
/*
var disqus_config = function () {
this.page.url = https://swatigupta1997.github.io/;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier disqus_YVOuNa8Mpc; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://swatiguptablog.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
  
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>

{% endif %}
