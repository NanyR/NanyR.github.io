---
layout: post
title:  Changing Perspective
date:   2017-05-22 04:08:35 +0000
---


I went to BrooklynJS this past week and was really inspired by one of the talks there from Patricia Realini. The talk was about CSS, but what I really liked was how Patricia portrayed the similarities between CSS and Art thinking about the history of art and the things that artists have been struggling with and looking for since the beginning of art as we know it. It is all about perspective and alignment. 

I started looking into creating the illusion of a 3D space, which essentially comes down to perspective. Two CSS properties that play a big part on that are transform and perspective.
Transform, if value is other than none, then the object it is targeting will act as a containining block for those elements in it with position fixed. The stacking content is basically the z-axis of the view port, elements can be 'stacked' in front of each other. You can achieve a lot of cool effects with the transform property and move an element to a desired angle or point on the page. There are a lot of options when it comes to transform, rotate, scale, skew; for 2D or 3D, 3D basically takes in a value for z whereas 2D just for x and y. 
Here is a very basic example of what you can do with transform, this is a series of divs with different rotating values:

![](http://res.cloudinary.com/dletp3dah/image/upload/c_scale,w_400/v1495421728/Screen_Shot_2017-05-21_at_10.53.27_PM_wymlgu.png)

The rotate functions rotate elements around corresponding axis. For example rotateX(n degrees) rotates an element around the x-axis, setting the top of the element back and away and the bottom of the element near, so essentially the sides of the element angle n degrees from the x-axis

```
.main{
  width: 200px;
  height: 200px;
  margin: 5em;
  transform: rotate3d(0, 3.0, 2.0, -20deg);
  background-color: rgba(232, 169, 168, 0.6)
}
#one{
  transform: rotate3d(0, 3.0, 2.0, 50deg);
}

#two{
   transform: rotate3d(0, 3.0, 2.0, -51deg);
  background-color: rgba(207, 137, 136, 0.4)
}
#three{
  transform: rotate3d(0, 3.0, 2.0,-90deg);
}

```


There is also the perspective property, which technicall activates the 3D space. With this you can set the distance of the z-plane from the viewer, in other words, you can make an objects look closer the higher the value of the perspective, or farther away as perspective gets lower. With perspective comes  the idea of a vanishing point which by default is at the center but you can move it with the perspective-origin property by giving it an x-axis and y-axis point. 
Transform-style defines how child elements will be rendered in a 3D space, values will be to either preserve its 3D space or to flatten it. 
Backface-visibility, elements have a transparent background, you can set it to visible or hidden; when visible, a mirror image of the object can be seen through.

![](http://res.cloudinary.com/dletp3dah/image/upload/v1495424877/Screen_Shot_2017-05-21_at_11.46.46_PM_wxqsqk.png)
```
.main{
  perspective: 300px;
  width: 300px;
  height: 300px;
  perspective-origin: 150% 150%;
  backface-visibility: visible;
  transform-style: preserve-3d;
  margin: 10em;
  background-color: rgba(232, 169, 168, 0.6)
}
.side{
  border: 2px solid black;
  width: 100px;
  height: 100px;
  position: absolute;
}

#two{
  transform: rotateY(180deg) translateZ(50px);
}
#three{
  transform: rotateY(90deg) translateZ(50px);
}
#four{
  transform: rotateY(-90deg) translateZ(50px);
}
```



![](http://res.cloudinary.com/dletp3dah/image/upload/v1495424854/Screen_Shot_2017-05-21_at_11.47.03_PM_jgj6zv.png)
```
.main{
  perspective: 300px;
  width: 300px;
  height: 300px;
  perspective-origin: 150% 150%;
  backface-visibility: visible;
  transform-style: preserve-3d;
  margin: 10em;

}
.side{
  border: 2px solid black;
  width: 100px;
  height: 100px;
  position: absolute;
}
#one{
  background-color: black;
}
#two{
  transform: rotateY(180deg) translateZ(50px);
}
#three{
  transform: rotateY(90deg) translateZ(50px);
}
#four{
  transform: rotateY(-90deg) translateZ(50px);
}
```

There is a lot more that you can do with these properties. Information can seem overwhleming, especially when dealing with z-axis, but I do recommend taking the time to review the documentation on these; I find the mozilla developer network site to be very clear and easy to understand. What is above is just the start of what is becoming a big interest of mine so I will definitely continue to play around with both of these properties and see what else I can come up with.

