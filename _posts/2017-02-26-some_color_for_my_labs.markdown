---
layout: post
title:  "Some color for my labs"
date:   2017-02-25 20:38:25 -0500
---


This past week we got to work with the internet. It was pretty cool to notice how we are connecting the dots on the concepts we have learned and practiced with for the first couple of weeks.
Seeing our work on the internet gives me some reassurance which is very much appreciated during these times of intense learning of abstract concepts. I am a visual learner, and seeing my code as a concrete product helps me make more sense of what is going on. Having said that, plain html is boring, and ugly, and being stuck for days on some of these labs tends to be frustrating and painful, especially when the site looks like craigslist.com so I decided to add some color and style to my labs.

The idea is to create a pretty basic css stylesheet to target things like background color, font and, in the case of this particular section of learn, forms. Having a layout.rb file is great to set up a template for all of my views. This is where you link the font and stylesheets (inside the head element)


![](https://res.cloudinary.com/dletp3dah/image/upload/v1488067827/Screen_Shot_2017-02-25_at_4.46.23_PM_ptwwqz.png)

To normalize or not...
normalize.css was created to remove default html styling inconsistencies between browsers so that you are styling from a specific, consistent html. It is definitely useful and important when it comes to larger projects, even though that is not the case with the labs, I did add a link to normalize.css on my html head for practice and just in case.
Also, order is important, normalize and fonts should be loaded before our css kicks in. 

Another thing I noticed, (and remembered from the readings) while trying to link my css files, was that just as with "views" sinatra knows that css files are included in the "/public" directory so linking it as "/public/main.css" will not render any styling and return a 404 not found for those particular files in the console. 

Once I had my css linked I just put together some css properties for the headers, added some round borders to the input fields to follow the roundness of the font, I added some margin on the page, and some styling for buttons. This definitely made a difference for me finishing the lab. 


![](https://res.cloudinary.com/dletp3dah/image/upload/v1488067591/nocss_pp7mwq.jpg)
![](https://res.cloudinary.com/dletp3dah/image/upload/v1488073662/Screen_Shot_2017-02-25_at_8.46.20_PM_m15vla.png)

Now, going into playlister, I will be adding the same css files. I made sure not to mess around with classes or ids since I know that the tests sometimes check for very specific attributes and I am not trying to add on another layer of complexity to my problem solving. I plan on using this as a template for now for the next couple of labs, I might change the colors every once in a while just for fun and to change it up. As I mentioned, I am a visual learner, and I care a lot (maybe too much) about aesthetics; seeing some color, a nice font, and some margin definitely makes a difference in my learning experience. 

