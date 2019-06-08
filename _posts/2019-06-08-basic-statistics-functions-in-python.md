---
layout: default
title: basic statistics functions in python
dates: 2019-06-08 14:30 IST
comments: true
---
# Basic statistics functions in python
Last Updated: {{ page.dates }}

Hello all!

Long time no see! Well, I was recently using some basic statistics functions in python (using pandas which is a very useful python library for data science), and felt that I should properly compile them here for easy future reference.

#### So, Lets get down to buisness!

First, import the pandas library in your jupyter notebook, and load your dataset as shown below. I am assuming the dataset to be one that contains student marks for various subjects, for ease of understanding.

```
import pandas as pd
df = pd.read_csv("data.csv")
df.head()
```

### Measures of central tendency:

#### Mode: 

```
df_mode = df['Marks'].mode(); df_mode
```

#### Median:

```
df_median = df['Marks'].median(); df_median
```

#### Mean:

```
df_mean = df['Marks'].mean(); df_mean
```

### Measures of data spread:

#### Range:

```
df_r = df['Marks'].max()-df['Marks'].min(); df_r
```

#### Inter-Quartile Range:

```
df_iqr = df['Marks'].quantile(0.75)-df['Marks'].quantile(0.25); df_iqr
```

#### Variance:

```
df_var = df['Marks'].var(ddof = 0); df_var
```

#### Standard Deviation:

```
df_std = df['Marks'].std(ddof = 0); df_std
```

#### Frequency distribution for categorical variables:

```
df_fd = df['Subject'].value_counts(); df_fd
```

#### Frequency distribution for continuous variables: 
visualization using histograms:

```
import matplotlib.pyplot as plt
%matplotlib inline
plt.hist(x='Marks', data=df, bins=5)
plt.show()
```

### Well, That's All for today, folks! See you next time.
Post your thoughts or additions to the list!

[Prev Entry](https://swatigupta1997.github.io/blog/2019/01/01/tips-to-create-github-blog/)



{% if page.comments %}

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = https://swatigupta1997.github.io/blog/2019/06/08/basic-statistics-functions-in-python/  // Replace PAGE_URL with your page's canonical URL variable
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
