---
layout: default
title: Creating your own blog series
dates: 2019-01-28 19:30 IST
comments: true
---
# Creating a blog using Github and Jkyell
Last Updated: {{ page.dates }}

Hello all!

I will kickstart with something that forms the very basis of this blog series. Yes, you guessed it right! <b><center>How to create a blog using Github (and Jekyll).</center></b>

You must be wondering, why use Github? Why not one of the numerous micro blogging sites available online (blogger, wordpress, medium etc.). They offers an extremely simple setup and smooth GUI experience. A lot less time spent on logistics right? 
Well, for one, Where is the fun in that? Afterall, we are coders!  Second, the whole point of this exercise is to explore and learn! So, why not learn how to actually create a blog from scratch as our starting point? Github is great in this aspect, as you will actually need to get your hands dirty, and understand how Jekyll works. <br />
Another personal reason is that using Github keeps all my things in one place, as the rest of my work is on Git as well, and this can be just one more repo.

#### So, Lets get down to buisness!

One easy way is to pull the repo by barryclark (https://github.com/barryclark/jekyll-now) and follow his instructions on minimally editing the repo to make it your own. While this is great for someone who does not want to spend time demistifying the logistics, again, that is not the point of this exercise.

So we will create our blog from scratch. (With guidance from barry clark ofc!)

#### PreRequisites: 
Not many, just be comfortable using Github, and basic html/markdown.

#### Some important details:
- Hey, What's Jekyll? : Jekyll is a parsing engine (written in ruby by Github's cofounder) used to build static websites from dynamic components such as templates, partials, liquid code, markdown, html, css etc. Jekyll is known as "a simple, blog aware, static site generator".
- We are not going to atempt something fancy here. If you are good with html/css, go ahead and add fancier elements to the blog/website. I will be using one of the already available themes.
- At any point, if you have a doubt, feel free to browse through my repo and see what to do yourself! Else, comment below!

- Step 1: Create your repository with the name: <username>.github.io 
- Step 2: create the default directory structure in the repo. This is mine:
  * _posts/
  * _layouts/
  * _config.yml
  * index.md
  * blog_home.html (optional, See Explanation)
  
#### Explanation: <br />
- index.md is the default landing page when 'username.github.io' is visited via url. You can directly make it your blog homepage or you can make this your personal website (like I did) and add a link to another page which can be your blog homepage (ref blog_home.html). 
- YAML file '_config.yml' contains all the configuration details of our site.
- The Directory '_posts/' is where all your blog entries will be kept. Naming convention for each blog entry: (year-month-day-title) (Ex: 2019-01-01-tips-to-create-github-blog.md) 
- The Directory '_layouts/' is where you will put your html layouts for customising the look of your pages/blog. You can have as many as you like, I will keep things simple and only use one, called 'default.html'. I took this layout from one of the themes that jekyll provides called 'jekyll-theme-cayman' and customised it for my purpose. 
 
Ok! Now that we have a grasp of the basic structure, we need to ensure that all things are in place, parameters configured. This is essentially done using the _config.yml file. Just add all the global variable values to it in the format:
<center>variable: value</center>
Then you can use these variable values anywhere using ('site.variable' enclosed in curly braces) format.
Some useful ones are:
- name 
- title
- theme
- permalink
- disqus
- markdown
- plugins
<br />
<p>
Out of all these, the one most essential to our blog implementation is permalink. You must set this parameter so jekyll can parse and assign urls to your blog entries (which are located in the _posts directory). It has to be such that each blog entry will get a unique url. </p>
 <br />
So it is a good idea to use a combination of date and blog-entry title to ensure uniqueness . 
My permalink setting is: 
<center> permalink: /blog/:year/:month/:day/:title/ </center>
Which is why, one of the blog entry url turns out to be: 
<center> https://swatigupta1997.github.io/blog/2019/01/01/tips-to-create-github-blog/ </center>
Do you now realize why we followed a convention in naming blog entries before? <br />
Yes, you are quite right, that is what gets parsed and provides the necessary info (:year :month :title etc.) to create unique url's for each blog entry!
<br /> <br />
Another important parameter to note is disqus. This is completely optional ofc. But what is a blog without reader comments?
I will briefly discuss how use this one. <br />
You first need to login to [Disqus](https://disqus.com/) (create an account if you are new.) Then follow the simple instructions there on how to 'Configure Disqus for Your Site'. Select jekyll as the platform when prompted. They will provide you with the universal code, which you can then embed at the end of your blog entries (after editing some config variables). Also, add your disqus shortname to _config.yml file under the disqus parameter. Voila! Comments are now enabled.
<br /> <br />
(The only doubt in this whole process that you may face is - what's a shortname? 
Actually, disqus clearly mentions it during the whole 'Configure Disqus for Your Site' process. If you somehow missed it, no worries. Try this: <br />
Go to the admin page of your account. Click on the settigs tab, then select the site you just created, ad access it's general settings. you will see your shortname!) <br />

Infact, there is a bit more efficient way to do this, so that you do not have to add the universal code to every blog entry:  Just create an _includes directory and putting the code there, then invoke it from your blog entry. I did not try this out, as I am too lazy. ;)
<br />
#### Some miscellenious info. 

Just like we configured global variables using the layouts.yml file, we can configure page specific variables using YAML front matter to every page by adding this at its beginning: 
<br />

```
---
layout: default
date: xx-xx-xxxx
title: xxxx
comments: true
# other options
---
```
<br />

These variables can then we accessed from within the page as page.variable enclosed in double curly braces . Here, the _layout_ variable is reserved and when set, will use the layout of the same name from layouts directory for that page.
<br />

## Well, That's All for today, folks! See you next time.
Post your doubts and I will try to clarify!

[Prev Entry](https://swatigupta1997.github.io/blog/2019/01/01/to-new-beginnings/)
<div style="text-align: right"> [Next Entry](https://swatigupta1997.github.io/blog/2019/06/08/basic-statistics-functions-in-python/) </div>


{% if page.comments %}

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = https://swatigupta1997.github.io/blog/2019/01/01/tips-to-create-github-blog/  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = {{ page.title }}; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://swatiguptablog-1.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            

{% endif %}

