---
author: W3 Schools
rating: C-WIP
genre: tech
---
# W3 JavaScript Tutorial (2021)
`SOURCE:` [source](https://www.w3schools.com/js/default.asp)
`TAGS:` #wip #article 
`AUTHOR:` W3 Schools

---
# JavaScript Introduction
The article says that [[JavaScript]] can change [[HTML]] content. It accepts both single and double quotes. 

```javascript
document.getElementById("demo").innerHTML = "Hello JavaScript";
```

The article provides another example, where we can change the value of the `src` attribute of an image. 

```html
<!DOCTYPE html>
<html>
	<body>
	
		<h2>What can JavaScript do?</h2>
		
		<p>JavaScript can change HTML attribute values. </p>
		
		<p>In this case JavaScript changes the value of the src (source) attribute of an image</p>
		
		<button
				onclick="document.getElementById('my_image').src='pic_bulb_on.gif'">Turn on the light</button>
		
		<img id='my_image' src = 'pic_bulb_off.gif'>Turn off the light</button>
	
	</body>
</html>
```

The above script creates a page with a title, represented by `<h2>`, followed by a few paragraphs and two buttons that can turn on and off a lignt, changing the image on the screen. 

> [!criticism]
> I think this tutorial kind of sucks. It doesn't really provide any context or information about what's happening, it just has a bunch of code. 