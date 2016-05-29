---
layout: post
title:  "一篇带有视频的文章"
date:   2016-03-15
excerpt: "经常写文章描述可以让你不再懒惰..."
tag:
- sample
- post
- video
comments: true
---

<iframe height="498" width="510" src="http://player.youku.com/embed/XMTI2MDI2ODQ4NA==" frameborder="0" ></iframe>

Video embeds are responsive and scale with the width of the main content block with the help of [FitVids](http://fitvidsjs.com/).

Not sure if this only effects Kramdown or if it's an issue with Markdown in general. But adding YouTube video embeds causes errors when building your Jekyll site. To fix add a space between the `<iframe>` tags and remove `allowfullscreen`. Example below:

{% highlight html %}
<iframe width="560" height="315" src="//www.youtube.com/embed/SU3kYxJmWuQ" frameborder="0"> </iframe>
{% endhighlight %}
