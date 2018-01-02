>So this attack should normally require some sort of encoding, but unfortunatley, gruyere is SUPER vulnerable, and the devs didnt try in the slightest, so the basic <script>alert(1)</script> works here 

>Notes: When trying encoding, its important to look at these styles (double %-encoding, bad UTF-8 encoding, HTML &-encoding, double &-encoding, and C-style encoding)

>Issue: Attempting to visit a completely unknown page will result in an error page being displayed, where the potential page is written on the error page. The problem here, is that it is done with no regard for what the requested page link actually was. So when we try to go to /<script>alert(1)</script>, the page is copying that text completely, then sticking it onto the error page as html and running the code between the 2 tags.

>Solution: Need to escape or cleanse all user input and variables before displaying them on a page.
