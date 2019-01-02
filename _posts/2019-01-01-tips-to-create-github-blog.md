---
layout: default
title: Creating your own blog series
comments: true
date: 2019-01-01
---
# Creating a blog using Github and Jkyell

Hello all!

I will kickstart this blog series by something that forms the very basis of this blog series. Yes, you guessed it right! <b><center>How to create a blog using Github (and Jekyll).</center></b>

You must be wondering, why Github? Why not the many blogging websites available online (blogger, wordpress, medium etc.), which offer an extremely simple setup and smooth GUI experience. A lot less time spent on logistics right? 
Well, for one, we are coders! Second, the whole point of this exercise is to explore and learn! So, why not learn how to actually create a blog from scratch as the starting point? Github is great in this aspect, as you will actually need to get your hands dirty. 
Another personal reason is that using Github keeps all my things in one place, as the rest of my work is on git as well, and this can be just one more repo.

So, Lets get down to buisness!

One easy way is to pull the repo by barryclark (https://github.com/barryclark/jekyll-now) and follow his instructions on minimally editing the repo to make it your own. While this is great for someone who doesnot want to spend time demistifying the logistics, again, that is not the point of this exercise.

So we will create our blog from scratch. (With guidance from barry clark ofc!)





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
