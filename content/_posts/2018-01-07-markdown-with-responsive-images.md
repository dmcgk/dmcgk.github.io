---
date: 2018-01-07 13:48:00 +00:00
---

I've never liked the overhead of dealing with responsive image sets in Markdown when writing for the web. I've set up this site to expect any image links as a simple list as part of the YAML header, rather than within the main body of the post, which is processed further by Jekyll at compile-time.

Since I only need to do this part once it can be as complex and edge-casey as I need while keeping the actual written content short and clean.

This works since I don't care about in-article image positioning. I'll either be sharing a single image or adding a single set of explanatory/descriptive images to the end of a post, rather than writing a print-style article with a strictly defined layout. 

For example, this Markdown+YAML file:

~~~ yaml
---
date: 2017-07-23 15:31:00 +01:00
images: 
    - 2017-07-23-chicago-broods.jpg
---

Chicago _broods_.
~~~

Becomes [this](/chicago-broods/), showing either a large or small file-size version of the image based on the viewing device type, without my needing to care about those variations when writing the post.

My live Jekyll code [is here]({{ site.markdown_url }}{{ site.github.repository_nwo }}/master/_includes/images.html) but to use it you'll still need to add multiple images to your site, appropriately named. I use @workflowhq on iOS to automate this part.
