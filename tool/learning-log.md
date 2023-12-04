# Tool Learning Log

Tool: **Kaboom**

Project: **Fate Platformer**

---

10/29/23:
* First I set up Kaboom by using the CDN, I simply did this by going to the setup document and pasting this into a index.html file I created for testing Kaboom:
``` js 
<script type="module">

// import kaboom lib
import kaboom from "https://unpkg.com/kaboom@3000.0.1/dist/kaboom.mjs";

// initialize kaboom context
kaboom();

// add a piece of text at position (120, 80)
add([
    text("hello"),
    pos(120, 80),
]);
</script>
```
* I also tinkered with the Kaboom Playground, it lets you choose different elements and components and gives you basic code that uses that specific element/component which you can change.
* I played around with the gravity component by changing the value of gravity which is a value that changes the rate an object moves in by pixels pers second
* I also tinkered by changing the key to jump instead of having space as the key I changed it to w
* Another thing I tinkered with is an ai element where you have an enemy that follows you and shoots you every so often which would kill you.
* I tinkered by changing some values and aspects of the entity making it faster and the bullets it shoots more accurate making it smarter and stronger.
---
12/3/23
Learning more elements in Kaboom
Kaboom introduces many components that can all be paired up with each other, so far during the work time I've spent on Monday this is what I learned
---
Platforms:
* Without a platform if you have a sprite that contains the body() component your sprite will have a physical body and without any platform it will keep falling.
* rect() renders a rectangle that accepts two arguments which include the width and height
* pos() meaning position can be given an x and y value like on a graph but in this case positioning the rectangle
* outline() self explanatory it assigns an outline to what you assign it with with a number like 4 being an outline of 4 pixels
* area() like body() but instead it gives something like a rectangle or whatever element it is a physical body which allows collisions with things like your sprite
* body({ isStatic: true }) What this does is makes the platform a static object meaning it doesn't move and that everything that doesn't move won't move past it either
* color(x, x, x) uses the RGB color system to assign colors to your platform or anything


add([
    rect(width(), 48),
    pos(0, height() - 48),
    outline(4),
    area(),
    body({ isStatic: true }),
    color(127, 200, 255),
])

Code here creates a platform using  all those components that is static in place and collideable with other physical elements like your sprite.
---
Condtions:
* Using an if statement we can create a condition where the sprite can only jump when it's grounded on the given platform
* We can use the component onKeyPress with an if statement where if that key is pressed the if statement will be ran
* onKeyPress("space", () => {
    if (bean.isGrounded()) {
        bean.jump();
    }
});
* Code above tells us that in the " " of onKeyPress is the key input
* The if statement runs the condition bean.isGrounded isGrounded is a function in the category of body that checks if the sprite is on a platform
* Now that the conditions are met it will run bean.jump(); which basically just allows the sprite to jump
---

X/X/X:
* Text


<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
