>If you look at one of the other repos I've got on here (the google_xss_cha lenge) you'll notice most of the xss attacks there are using a similar method to what I use here. The "classic" (in my world) <img> with onerror attribute. Its important to note here that, if you look at the source code (https://google-gruyere.appspot.com/code), you will find a list of tags and attributes that are NOT allowed. "onerror" is not one of them, so I chose that. Although, after doing so, onmouseover is probably a better solution so that you are not bombarded with alert boxes everytime you visit the page... 

>Issue: Allowing users to input their own tags and not properly stripping/sanitzing them is just down right awful. Things like &lt;img src='BLAH' onerror=alert(1)&gt; are just brutal.

>Solution:Sanitize all user input thoroughly.
