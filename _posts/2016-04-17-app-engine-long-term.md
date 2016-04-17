---
layout: post
title: Long-Term AppEngine Development
---

I've had the chance to talk about my experiences with [Google App Engine][gae] at a recent [local GDG meetup][meetup]. It was fun, because it was the first time I presented in front of people who were very new to the topic. This talk gave me a chance to think about my history with App Engine and how I've been using it. Here are the slides, thoughts after the fold.

<iframe src="https://docs.google.com/presentation/d/1jfcL4YtpVFLOrz6SgnuRYTQe5CJYmWZkQ23wUOzCZuc/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
<br/>

My first experience with App Engine was shortly after its public availability in 2008. I used it for an academic project: as a proof of concept of my master thesis on software requirements. I also wanted to learn Python and play around with something new. The other cool thing I got to use at that time was [Yahoo Pipes][pipes], which only recently, in summer of 2015, was shut down.

Since that time, the App Engine platform has progressed a lot and keeps improving. We've been using it for JS error logging in the web frontend at [Trayn][trayn] with only minimal maintenance overhead for the last few years. See the deployment cycles in the slides on page 14 for an example of how often we had to do something with the application.

Last month, among several announcements during [GCP Next 2016][gcp-next], _Managed VMs_ were rebranded as [_Flexible Environment_][gae-flexible]. The now so-called [_Standard Environment_][gae-standard] is still an impressive piece of technology, but for me, more than that, encapsulates the web architecture and mindset we now all rely on when we use App Engine or similar platform. I hope I can follow up with some details at a later point in time.

Until then, I will try to collect my thoughts in upcoming posts and [at this location]({{ site.url }}/articles#app-engine).


[gae-flexible]: https://cloud.google.com/appengine/docs/flexible/
[gae-standard]: https://cloud.google.com/appengine/docs/about-the-standard-environment
[gae]: https://cloud.google.com/appengine/
[gcp-next]: https://cloudplatformonline.com/Next2016.html
[meetup]: http://www.meetup.com/GDG-Vienna/events/229686731/
[pipes]: https://en.wikipedia.org/wiki/Yahoo!_Pipes
[trayn]: http://www.trayn.com
