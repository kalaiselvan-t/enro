---
layout: post
title: Automatic verification of neural networks based object detection modules
image:
    path: /assets/img/blog/automatic-verification-home.jpg
description: >
  Master thesis project for the degree program M.Sc Autonomous Systems in colloboration with ThoughtWorks
sitemap: true
comments: true
---
{:.lead}

- Table of Contents
{:toc .large-only}

Let me start by asking you this question. Do you know if the neural network you developed work as you intended? You might have used a verification dataset to check if your model has generalized well to unseen data. But is that enough to know if the neural network's functionality is correct. What if the network is going to be deployed in a safety ctitical system like autonomous cars? It is absolutely necessary to make sure that they have correct functionality before we can deploy such systems. What can we do to make sure our network doesn't exhibit any unintended behaviours after deployment.

Automotive industry is very well regulated by both the government and industry consortiums. It follows the V-model development cycle for its systems development. One of the important processes


## What is Verification and Validation?

This is done by a process called verification and validation.

{% if page.comments %}
<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    /*
    var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = 'https://ks-disqus-com.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}