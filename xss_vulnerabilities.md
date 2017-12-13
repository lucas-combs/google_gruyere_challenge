FILE UPLOAD XSS:
>I uploaded a .html file, that is available at this url:
>https://google-gruyere.appspot.com/486377097659982405127477087299296425597/xss_vulns/exploit.html

>Issue: The idea behind this exploit is that you can get someone to click this link, which will cause them to unknowingly open up and run whatever code you've written it (malicious or not). Its quite devious, as it appears to be coming from a potential trusted source.

>Solution: Host the file on a different domain, so that its easy to tell if the file/page/link is coming from a trusted source, or a different one.

REFLECTED XSS:
>So this attack should normally require some sort of encoding, but unfortunatley, gruyere is SUPER vulnerable, and the devs didnt try in the slightest, so the basic <script>alert(1)</script> works here

>Notes: When trying encoding, its important to look at these styles (double %-encoding, bad UTF-8 encoding, HTML &-encoding, double &-encoding, and C-style encoding)

>Issue: Attempting to visit a completely unknown page will result in an error page being displayed, where the potential page is written on the error page. The problem here, is that it is done with no regard for what the requested page link actually was. So when we try to go to /<script>alert(1)</script>, the page is copying that text completely, then sticking it onto the error page as html and running the code between the 2 tags.

>Solution: Need to escape or cleanse all user input and variables before displaying them on a page.

STORED XSS:
>If you look at one of the other repos I've got on here (the google_xss_challenge) you'll notice most of the xss attacks there are using a similar method to what I use here. The "classic" <img> with onerror attribute. Its important to note here that, if you look at the source code (https://google-gruyere.appspot.com/code), you will find a list of tags and attributes that are NOT allowed. "onerror" is not one of them, so I chose that. Although, after doing so, onmouseover is probably a better solution so that you are not bombarded with alert boxes everytime you visit the page...

>Issue:Allowing users to input their own tags and not properly stripping/sanitzing them is just down right awful. Things like &lt;img src='BLAH' onerror=alert(1)&gt; are just brutal

>Solution:Sanitize all user input thoroughly. 
