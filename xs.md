# Assignment 5 - xs - Noah Lee - October 23rd 2024

## Part 1: Cookies
a. Go to FDF and use your browser's Inspector to take a look at your cookies for cs338.jeffondich.com. Are there cookies for that domain? What are their names and values? \
b. Using the "Theme" menu on the FDF page, change your theme to red or blue. Look at your cookies for cs338.jeffondich.com again. Did they change? \
c. Do the previous two steps (examining cookies and changing the theme) using Burpsuite. What "Cookie:" and "Set-Cookie:" HTTP headers do you see? Do you see the same cookie values as you did with the Inspector? \
d. Quit your browser, relaunch it, and go back to the FDF. Is your red or blue theme (wherever you last left it) still selected? \
e. How is the current theme transmitted between the browser and the FDF server? \
f. When you change the theme, how is the change transmitted between the browser and the FDF server? \
g. How could you use your browser's Inspector to change the FDF theme without using the FDF's Theme menu? \
h. How could you use Burpsuite's Proxy tool to change the FDF theme without using the FDF's Theme menu? \
i. Where does your OS (the OS where you're running your browser and Burpsuite, that is) store cookies? (This will require some internet searching, most likely.) 

1a. 
I see one cookie. name = "theme", value = "blue". \
b.
I changed my theme to red. It changed the value to "red" \
c.
In the response, I see "Set-Cookie: theme=default; expires ..." and in request, I see "Cookie: theme=default" It is the same as on my inspector, but the theme is different, because I changed it on my browser. \
d. It is still the same color (red) \
e. The browser, in the request sends as a header in the HTTP request for /fdf, "Cookie: theme=red" when I open it again. \
f. The cookie is updated using "Set-Cookie: theme=red" when I changed it from default. \
g. Updating the cookie's value in inspector (eg. to blue) and then reloading the page changes the theme. \
h.  By reloading the page and modifying the GET paramater for the theme and the cookie value. \
i. ~/Library/Application\ Support/Google/Chrome (for google chrome)

## Part 2: Cross-site Scripting (XSS)
Questions:\
a. Provide a diagram and/or a step-by-step description of the nature and timing of Moriarty's attack on users of the FDF. Note that some of the relevant actions may happen long before other actions.\
b. Describe an XSS attack that is more virulent than Moriarty's "turn something red" and "pop up a message" attacks. Think about what kinds of things the Javascript might have access to via Alice's browser when Alice views the attacker's post.\
c. Do it again: describe a second attack that is more virulent than Moriarty's, but that's substantially different from your first idea. \
d. What techniques can the server or the browser use to prevent what Moriarty is doing?

a. \
1) Moriarty makes a forum post on FDF, injecting JS code using a script tag in their post. 
2) Later on, when Bob visits FDF and opens Moriarty's post, because FDF has not prevented script tags from being read by the browser, the javascript that Moriarty has been injected runs on Bob's browser.
3) This javascript may be used for very malicious purposes, like changing Bob's cookies, or performing unauthorized actions on Bob's computer.
4) This post remains on FDF, and can effect any other users who click on the post in the future.

b. \
Cookie theft:
When Bob visits Moriarty's forum post, an XSS script runs which allows Moriarty to read all of Bob's recent cookies. This gives Moriarty insight as to the websites that Bob has been visiting and maybe even some private information on Bob like what is in his shopping cart or other personal information.

c. \
Slow down your computer:
To mess with Bob, Moriarty can inject malicious code that runs billions of instances of a snake game, making Bob's computer run extremely slow and maybe even crashing his computer. This is similar to a DOS attack but could potentially escalate to permanent damage to Bob's computer if Moriarty injects a virus or some other malicious software onto Bob's machine.

d. \
On the server side (jeff), input sanitation can be used to ensure HTML tags can not be in other people's posts or to just render all of it as text. On the client side (Bob), Bob can ensure his browser has XSS protection, where the browser can detect potential malicious scripts which have been injected and block them from running on Bob's computer