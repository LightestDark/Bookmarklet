# Bookmarklet
reader mode bookmarklet — click it on any cluttered webpage and it extracts just the article text, clean and readable. buttons in the top right let you switch to dark mode (black + yellow), bump the font size up, cycle through rainbow backgrounds every 2 seconds, or drop a cat in the middle of the screen. c


Devlog

May 22
Started this for Hacklet. Idea was simple just strip a webpage down to the article and nothing else. Got the basic content scoring working tonight, it looks at class names and tag types to guess where the real text is. Works pretty well on BBC and Medium

May 23
Added the toolbar. Three buttons top right, close dark mode and A+. Dark mode flips the background black and text yellow which looks sick actually. Close restores the whole page back to how it was
Had an annoying bug where the buttons would disappear on some sites, turned out React sites were re-rendering the body and wiping everything I injected. Fixed it by appending the bar last after all the content swap

May 24
A+ wasnt working on most pages. Sites were overriding the font size with their own !important rules so my change was getting ignored. Fixed it by setting the style directly on the element instead of through a stylesheet
Also changed the dark mode button label to actually say "light mode" when its in dark mode. Seemed obvious in hindsight

May 25
Added rainbow mode. Cycles through 8 pastel colours every 2 seconds. Took longer than expected because I was storing the timer inside the state object which kept getting overwritten so the interval was dying immediately. Moved it to a closure variable and it works fine now
Rainbow and dark mode cancel each other out if you toggle one while the others on

May 26
Added the cat button. Pulls a random image from placekitten and pins it dead centre with a dark backdrop. First tried cataas.com but it gets blocked by CSP headers on basically every real site so switched
If the image fails to load it falls back to 😽 at 200px. Honestly the fallback might be better than the actual cat

May 27
Cleaned everything up and made it into a proper repo. Wrote the README, tested it on a bunch of sites. Works well on most news sites and blogs. Wikipedia is a bit weird but still readable
Submitting to Hacklet this week
